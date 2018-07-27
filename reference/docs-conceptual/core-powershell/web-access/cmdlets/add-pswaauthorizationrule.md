---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: bcf897730881551ec16ce970de6a1330961b67e6
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268269"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="3bc50-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3bc50-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="3bc50-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="3bc50-104">SYNOPSIS</span></span>

<span data-ttu-id="3bc50-105">Dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="3bc50-105">Adds a new authorization rule to the Windows PowerShell Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bc50-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bc50-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="3bc50-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="3bc50-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="3bc50-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="3bc50-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="3bc50-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="3bc50-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="3bc50-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="3bc50-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="3bc50-111">OPIS</span><span class="sxs-lookup"><span data-stu-id="3bc50-111">DESCRIPTION</span></span>

<span data-ttu-id="3bc50-112">**Add-PswaAuthorizationRule** polecenie cmdlet dodaje nową regułę autoryzacji do zestawu reguł autoryzacji dostępu do sieci Web PowerShell(r) Windows.</span><span class="sxs-lookup"><span data-stu-id="3bc50-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell(r) Web Access authorization rule set.</span></span>

<span data-ttu-id="3bc50-113">Należy określić użytkowników, komputerów i punkty końcowe programu Windows PowerShell, dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="3bc50-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="3bc50-114">Można określić użytkowników i komputerów indywidualne konta użytkowników i nazwy komputerów lub za pomocą określania grup.</span><span class="sxs-lookup"><span data-stu-id="3bc50-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="3bc50-115">Na komputerze, który jest przyłączony do domeny usługi Active Directory polecenie cmdlet używa identyfikator zabezpieczeń (SID) komputera, aby utworzyć regułę.</span><span class="sxs-lookup"><span data-stu-id="3bc50-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span> <span data-ttu-id="3bc50-116">Dzięki temu można używać krótką nazwę, w pełni kwalifikowaną nazwę domeny (FQDN) lub adres IP dla **nazwy komputera** pola na stronie logowania.</span><span class="sxs-lookup"><span data-stu-id="3bc50-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="3bc50-117">Na komputerze, który nie jest przyłączony do domeny usługi Active Directory polecenie cmdlet tworzy regułę przy użyciu nazwy komputera, dostarczone przez administratora.</span><span class="sxs-lookup"><span data-stu-id="3bc50-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="3bc50-118">Do pomyślnego połączenia z tą maszyną, użytkownik końcowy należy podać nazwę komputera, dokładnie tak, jak wygląda na to, w regule.</span><span class="sxs-lookup"><span data-stu-id="3bc50-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="3bc50-119">W przypadku wielu komputerów w ramach tej samej nazwie w sieci krótką nazwę może prowadzić do więcej niż jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3bc50-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="3bc50-120">Może to prowadzić do niejednoznaczności podczas nawiązywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="3bc50-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="3bc50-121">Na przykład, jeśli istnieje reguła komputera grupy roboczej, o nazwie "*serwer1*" i nowy komputer o nazwie *server1.contoso.com* jest dołączony do sieci, zakończy się pomyślnie weryfikacji przy użyciu reguł autoryzacji i Windows PowerShell Web Access próbuje nawiązać połączenie z komputera o nazwie "*serwer1*".</span><span class="sxs-lookup"><span data-stu-id="3bc50-121">For example, if a rule exists for the workgroup computer named "*Server1*" and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named "*Server1*".</span></span> <span data-ttu-id="3bc50-122">Nie ma żadnej gwarancji, połączenie jest nawiązywane z określonej grupy roboczej komputera; Nie można ustanowić w grupie roboczej lub na komputerze domeny o nazwie "*serwer1*".</span><span class="sxs-lookup"><span data-stu-id="3bc50-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="3bc50-123">Aby ograniczyć niejednoznaczność, zalecane jest, użyj nazwy FQDN dla komputera docelowego, jeśli to możliwe utworzyć regułę autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="3bc50-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="3bc50-124">Reguły autoryzacji oceny podstawowego poświadczenia logowania użytkowników programu Windows PowerShell Web Access, a nie poświadczeń alternatywnych (drugi zestaw poświadczeń znaleziony w **opcjonalne ustawienia połączenia** sekcji Strona logowania).</span><span class="sxs-lookup"><span data-stu-id="3bc50-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="3bc50-125">Aby na przykład Zobacz przykład 6.</span><span class="sxs-lookup"><span data-stu-id="3bc50-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="3bc50-126">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bc50-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="3bc50-127">-ComputerGroupName \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="3bc50-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="3bc50-128">Określa nazwę grupy komputerów w Active Directory Domain Services (AD DS) lub grupy lokalne, do których ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="3bc50-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-129">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-129">Aliases</span></span>                     | <span data-ttu-id="3bc50-130">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-130">none</span></span>                  |
| <span data-ttu-id="3bc50-131">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-131">Required?</span></span>                   | <span data-ttu-id="3bc50-132">true</span><span class="sxs-lookup"><span data-stu-id="3bc50-132">true</span></span>                  |
| <span data-ttu-id="3bc50-133">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-133">Position?</span></span>                   | <span data-ttu-id="3bc50-134">o nazwie</span><span class="sxs-lookup"><span data-stu-id="3bc50-134">named</span></span>                 |
| <span data-ttu-id="3bc50-135">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-135">Default Value</span></span>               | <span data-ttu-id="3bc50-136">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-136">none</span></span>                  |
| <span data-ttu-id="3bc50-137">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-137">Accept Pipeline Input?</span></span>      | <span data-ttu-id="3bc50-138">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="3bc50-138">True (ByPropertyName)</span></span> |
| <span data-ttu-id="3bc50-139">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-139">Accept Wildcard Characters?</span></span> | <span data-ttu-id="3bc50-140">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-140">false</span></span>                 |

### <a name="-computername-string"></a><span data-ttu-id="3bc50-141">-ComputerName \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="3bc50-141">-ComputerName \<String\></span></span>

<span data-ttu-id="3bc50-142">Określa nazwę komputera, do której ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="3bc50-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-143">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-143">Aliases</span></span>                     | <span data-ttu-id="3bc50-144">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-144">none</span></span>                  |
| <span data-ttu-id="3bc50-145">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-145">Required?</span></span>                   | <span data-ttu-id="3bc50-146">true</span><span class="sxs-lookup"><span data-stu-id="3bc50-146">true</span></span>                  |
| <span data-ttu-id="3bc50-147">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-147">Position?</span></span>                   | <span data-ttu-id="3bc50-148">o nazwie</span><span class="sxs-lookup"><span data-stu-id="3bc50-148">named</span></span>                 |
| <span data-ttu-id="3bc50-149">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-149">Default Value</span></span>               | <span data-ttu-id="3bc50-150">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-150">none</span></span>                  |
| <span data-ttu-id="3bc50-151">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-151">Accept Pipeline Input?</span></span>      | <span data-ttu-id="3bc50-152">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="3bc50-152">True (ByPropertyName)</span></span> |
| <span data-ttu-id="3bc50-153">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-153">Accept Wildcard Characters?</span></span> | <span data-ttu-id="3bc50-154">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-154">false</span></span>                 |

### <a name="-configurationname-string"></a><span data-ttu-id="3bc50-155">ConfigurationName — \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="3bc50-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="3bc50-156">Określa nazwę konfiguracji sesji programu Windows PowerShell, nazywane również obszar działania, do której ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="3bc50-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-157">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-157">Aliases</span></span>                     | <span data-ttu-id="3bc50-158">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-158">none</span></span>                  |
| <span data-ttu-id="3bc50-159">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-159">Required?</span></span>                   | <span data-ttu-id="3bc50-160">true</span><span class="sxs-lookup"><span data-stu-id="3bc50-160">true</span></span>                  |
| <span data-ttu-id="3bc50-161">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-161">Position?</span></span>                   | <span data-ttu-id="3bc50-162">o nazwie</span><span class="sxs-lookup"><span data-stu-id="3bc50-162">named</span></span>                 |
| <span data-ttu-id="3bc50-163">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-163">Default Value</span></span>               | <span data-ttu-id="3bc50-164">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-164">none</span></span>                  |
| <span data-ttu-id="3bc50-165">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-165">Accept Pipeline Input?</span></span>      | <span data-ttu-id="3bc50-166">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="3bc50-166">True (ByPropertyName)</span></span> |
| <span data-ttu-id="3bc50-167">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-167">Accept Wildcard Characters?</span></span> | <span data-ttu-id="3bc50-168">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-168">false</span></span>                 |

### <a name="-credential--pscredential"></a><span data-ttu-id="3bc50-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="3bc50-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="3bc50-170">Określa **PSCredential** obiektu dla konta użytkownika, który chcesz użyć, aby zmienić reguły autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="3bc50-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="3bc50-171">Jeśli ten parametr nie zostanie dodany, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3bc50-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="3bc50-172">Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby dodać reguły autoryzacji zdalnie, uruchom [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3bc50-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-173">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-173">Aliases</span></span>                     | <span data-ttu-id="3bc50-174">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-174">none</span></span>  |
| <span data-ttu-id="3bc50-175">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-175">Required?</span></span>                   | <span data-ttu-id="3bc50-176">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-176">false</span></span> |
| <span data-ttu-id="3bc50-177">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-177">Position?</span></span>                   | <span data-ttu-id="3bc50-178">o nazwie</span><span class="sxs-lookup"><span data-stu-id="3bc50-178">named</span></span> |
| <span data-ttu-id="3bc50-179">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-179">Default Value</span></span>               | <span data-ttu-id="3bc50-180">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-180">none</span></span>  |
| <span data-ttu-id="3bc50-181">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-181">Accept Pipeline Input?</span></span>      | <span data-ttu-id="3bc50-182">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-182">false</span></span> |
| <span data-ttu-id="3bc50-183">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-183">Accept Wildcard Characters?</span></span> | <span data-ttu-id="3bc50-184">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-184">false</span></span> |

### <a name="-force"></a><span data-ttu-id="3bc50-185">-Force</span><span class="sxs-lookup"><span data-stu-id="3bc50-185">-Force</span></span>

<span data-ttu-id="3bc50-186">Wymusza uruchomienie polecenia bez wyświetlenia monitu o potwierdzenie przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3bc50-186">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="3bc50-187">Ponadto on również monituje o potwierdzenie po wprowadzeniu nazwy komputera prostej lub krótki (takie jak nazwa, która nie jest nazwą domeny lub nie jest w pełni kwalifikowana).</span><span class="sxs-lookup"><span data-stu-id="3bc50-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="3bc50-188">Potwierdzenie jest wymagany ze względów bezpieczeństwa, dzięki czemu można użyć prostą nazwę, aby dodać komputer tylko wtedy, gdy komputer znajduje się w grupie roboczej.</span><span class="sxs-lookup"><span data-stu-id="3bc50-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-189">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-189">Aliases</span></span>                              | <span data-ttu-id="3bc50-190">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-190">none</span></span>                                 |
| <span data-ttu-id="3bc50-191">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-191">Required?</span></span>                            | <span data-ttu-id="3bc50-192">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-192">false</span></span>                                |
| <span data-ttu-id="3bc50-193">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-193">Position?</span></span>                            | <span data-ttu-id="3bc50-194">o nazwie</span><span class="sxs-lookup"><span data-stu-id="3bc50-194">named</span></span>                                |
| <span data-ttu-id="3bc50-195">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-195">Default Value</span></span>                        | <span data-ttu-id="3bc50-196">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-196">none</span></span>                                 |
| <span data-ttu-id="3bc50-197">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3bc50-198">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-198">false</span></span>                                |
| <span data-ttu-id="3bc50-199">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3bc50-200">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="3bc50-201">-RuleName \<ciągu\></span><span class="sxs-lookup"><span data-stu-id="3bc50-201">-RuleName \<String\></span></span>

<span data-ttu-id="3bc50-202">Określa przyjazną nazwę dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="3bc50-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-203">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-203">Aliases</span></span>                              | <span data-ttu-id="3bc50-204">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-204">none</span></span>                                 |
| <span data-ttu-id="3bc50-205">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-205">Required?</span></span>                            | <span data-ttu-id="3bc50-206">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-206">false</span></span>                                |
| <span data-ttu-id="3bc50-207">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-207">Position?</span></span>                            | <span data-ttu-id="3bc50-208">o nazwie</span><span class="sxs-lookup"><span data-stu-id="3bc50-208">named</span></span>                                |
| <span data-ttu-id="3bc50-209">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-209">Default Value</span></span>                        | <span data-ttu-id="3bc50-210">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-210">none</span></span>                                 |
| <span data-ttu-id="3bc50-211">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3bc50-212">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="3bc50-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="3bc50-213">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3bc50-214">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="3bc50-215">-UserGroupName \<ciągu\[\]\></span><span class="sxs-lookup"><span data-stu-id="3bc50-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="3bc50-216">Określa nazwę co najmniej jednej grupy użytkowników w usługach AD DS i grupy lokalne, do których ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="3bc50-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-217">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-217">Aliases</span></span>                              | <span data-ttu-id="3bc50-218">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-218">none</span></span>                                 |
| <span data-ttu-id="3bc50-219">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-219">Required?</span></span>                            | <span data-ttu-id="3bc50-220">true</span><span class="sxs-lookup"><span data-stu-id="3bc50-220">true</span></span>                                 |
| <span data-ttu-id="3bc50-221">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-221">Position?</span></span>                            | <span data-ttu-id="3bc50-222">o nazwie</span><span class="sxs-lookup"><span data-stu-id="3bc50-222">named</span></span>                                |
| <span data-ttu-id="3bc50-223">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-223">Default Value</span></span>                        | <span data-ttu-id="3bc50-224">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-224">none</span></span>                                 |
| <span data-ttu-id="3bc50-225">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3bc50-226">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="3bc50-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="3bc50-227">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3bc50-228">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="3bc50-229">-UserName \<ciągu\[\]\></span><span class="sxs-lookup"><span data-stu-id="3bc50-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="3bc50-230">Określa co najmniej jednego użytkownika, do których ta reguła udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="3bc50-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="3bc50-231">Nazwa użytkownika może mieć konto użytkownika lokalnego na komputerze bramy lub użytkownika w usługach AD DS.</span><span class="sxs-lookup"><span data-stu-id="3bc50-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span> <span data-ttu-id="3bc50-232">Format jest `domain\user` lub `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="3bc50-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="3bc50-233">Aliasy</span><span class="sxs-lookup"><span data-stu-id="3bc50-233">Aliases</span></span>                              | <span data-ttu-id="3bc50-234">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-234">none</span></span>                                 |
| <span data-ttu-id="3bc50-235">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="3bc50-235">Required?</span></span>                            | <span data-ttu-id="3bc50-236">true</span><span class="sxs-lookup"><span data-stu-id="3bc50-236">true</span></span>                                 |
| <span data-ttu-id="3bc50-237">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="3bc50-237">Position?</span></span>                            | <span data-ttu-id="3bc50-238">1</span><span class="sxs-lookup"><span data-stu-id="3bc50-238">1</span></span>                                    |
| <span data-ttu-id="3bc50-239">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="3bc50-239">Default Value</span></span>                        | <span data-ttu-id="3bc50-240">brak</span><span class="sxs-lookup"><span data-stu-id="3bc50-240">none</span></span>                                 |
| <span data-ttu-id="3bc50-241">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="3bc50-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3bc50-242">Wartość true (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="3bc50-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="3bc50-243">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="3bc50-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3bc50-244">false</span><span class="sxs-lookup"><span data-stu-id="3bc50-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="3bc50-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="3bc50-245">\<CommonParameters\></span></span>

<span data-ttu-id="3bc50-246">To polecenie cmdlet obsługuje typowe parametry:</span><span class="sxs-lookup"><span data-stu-id="3bc50-246">This cmdlet supports the common parameters:</span></span>

<span data-ttu-id="3bc50-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer i -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="3bc50-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="3bc50-248">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="3bc50-248">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="3bc50-249">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="3bc50-249">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="3bc50-250">Ciąg</span><span class="sxs-lookup"><span data-stu-id="3bc50-250">String</span></span>

<span data-ttu-id="3bc50-251">To polecenie cmdlet przyjmuje ciągiem lub tablicą ciągów jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="3bc50-251">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="3bc50-252">Ciąg\[\]</span><span class="sxs-lookup"><span data-stu-id="3bc50-252">String\[\]</span></span>

<span data-ttu-id="3bc50-253">To polecenie cmdlet przyjmuje ciągiem lub tablicą ciągów jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="3bc50-253">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="3bc50-254">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3bc50-254">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="3bc50-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3bc50-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="3bc50-256">To polecenie cmdlet zwraca obiekt reguły autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="3bc50-256">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="3bc50-257">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="3bc50-257">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="3bc50-258">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="3bc50-258">EXAMPLE 1</span></span>

<span data-ttu-id="3bc50-259">W tym przykładzie daje dostęp do konfiguracji sesji _Punktkoncowypswa_, ograniczonym obszarem działania, na _srv2_ dla użytkowników w _SMAdmins_ grupy.</span><span class="sxs-lookup"><span data-stu-id="3bc50-259">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="3bc50-260">Nazwa komputera musi być w pełni kwalifikowaną nazwę domeny (FQDN).</span><span class="sxs-lookup"><span data-stu-id="3bc50-260">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="3bc50-261">Administratorzy zdefiniować konfigurację sesji z ograniczonym lub obszaru działania, czyli ograniczonym zakresem poleceń cmdlet i zadań, które użytkownicy końcowi mogą być uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="3bc50-261">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="3bc50-262">Definiowanie ograniczonym obszarem działania można uniemożliwić użytkownikom uzyskanie dostępu do innych komputerów, które są nie w obszarze dozwolone działania Windows PowerShell(r) związku z tym oferują bardziej bezpiecznego połączenia.</span><span class="sxs-lookup"><span data-stu-id="3bc50-262">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell(r) runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="3bc50-263">Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](/powershell/module/microsoft.powershell.core/about/about_session_configurations) lub [instalacji i użyj Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="3bc50-263">For more information on session configurations, see [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) or [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="3bc50-264">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="3bc50-264">EXAMPLE 2</span></span>

<span data-ttu-id="3bc50-265">W tym przykładzie daje dostęp do domyślnej konfiguracji sesji programu Windows PowerShell, `Microsoft.PowerShell`na *srv2* dla użytkowników w użytkowników o nazwie `contoso\user1`, `contoso\user2`, i `contoso\user3`.</span><span class="sxs-lookup"><span data-stu-id="3bc50-265">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="3bc50-266">To polecenie cmdlet tworzy trzy reguły (1 na osobę).</span><span class="sxs-lookup"><span data-stu-id="3bc50-266">This cmdlet creates three rules (1 per person).</span></span>

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="3bc50-267">PRZYKŁAD 3</span><span class="sxs-lookup"><span data-stu-id="3bc50-267">EXAMPLE 3</span></span>

<span data-ttu-id="3bc50-268">W tym przykładzie pokazano, jak wprowadzanie wartości nazwy użytkownika przy użyciu potoku.</span><span class="sxs-lookup"><span data-stu-id="3bc50-268">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="3bc50-269">PRZYKŁAD 4</span><span class="sxs-lookup"><span data-stu-id="3bc50-269">EXAMPLE 4</span></span>

<span data-ttu-id="3bc50-270">Ten przykład ilustruje jak wszystkie parametry pobierają wartości z potoku, według nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="3bc50-270">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="3bc50-271">PRZYKŁAD 5</span><span class="sxs-lookup"><span data-stu-id="3bc50-271">EXAMPLE 5</span></span>

<span data-ttu-id="3bc50-272">Ten przykład dodaje regułę zezwalającą na użytkownika lokalnego o nazwie `PswaServer\ChrisLocal` dostęp do serwera o nazwie **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="3bc50-272">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="3bc50-273">W tym przykładzie przedstawiono scenariusz, w którym brama znajduje się w grupie roboczej i komputer docelowy znajduje się w domenie.</span><span class="sxs-lookup"><span data-stu-id="3bc50-273">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="3bc50-274">Reguła autoryzacji ma zastosowanie do użytkowników lokalnych skonfigurowanych na bramie.</span><span class="sxs-lookup"><span data-stu-id="3bc50-274">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="3bc50-275">W witrynie programu Windows PowerShell Web Access logowania w celu pomyślnego uwierzytelnienia użytkownik musi podać drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** obszaru.</span><span class="sxs-lookup"><span data-stu-id="3bc50-275">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="3bc50-276">Serwer bramy zastosuje ten dodatkowy zestaw poświadczeń do uwierzytelniania użytkownika na komputerze docelowym, a serwer o nazwie *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="3bc50-276">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="3bc50-277">PRZYKŁAD 6</span><span class="sxs-lookup"><span data-stu-id="3bc50-277">EXAMPLE 6</span></span>

<span data-ttu-id="3bc50-278">Ten przykład umożliwia wszystkim użytkownikom dostęp do wszystkich punktów końcowych na wszystkich komputerach.</span><span class="sxs-lookup"><span data-stu-id="3bc50-278">This example allows all users access to all endpoints on all computers.</span></span> <span data-ttu-id="3bc50-279">Wyłącza to zasadniczo reguły autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="3bc50-279">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="3bc50-280">Korzystanie z `*` znak symbolu wieloznacznego nie jest zalecane w przypadku wdrożeń z istotnymi dla zabezpieczeń i tylko powinny być traktowane jako dla środowisk testowych lub używane we wdrożeniach, których bezpieczeństwo może zostać złagodzone.</span><span class="sxs-lookup"><span data-stu-id="3bc50-280">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="3bc50-281">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bc50-281">See Also</span></span>

<span data-ttu-id="3bc50-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="3bc50-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="3bc50-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="3bc50-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="3bc50-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="3bc50-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="3bc50-285">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="3bc50-285">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="3bc50-286">Dodawanie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3bc50-286">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="3bc50-287">New-Object</span><span class="sxs-lookup"><span data-stu-id="3bc50-287">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="3bc50-288">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="3bc50-288">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)