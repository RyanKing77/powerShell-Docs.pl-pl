---
description: 
ms.topic: article
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 2016-12-12
title: Dodaj pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 196797215a678e6f674592dc6b289816aced3c01
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="9196b-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9196b-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="9196b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9196b-104">SYNOPSIS</span></span>

<span data-ttu-id="9196b-105">Dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="9196b-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="9196b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9196b-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="9196b-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="9196b-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="9196b-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="9196b-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="9196b-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="9196b-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="9196b-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="9196b-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="9196b-111">OPIS</span><span class="sxs-lookup"><span data-stu-id="9196b-111">DESCRIPTION</span></span>

<span data-ttu-id="9196b-112">**Add-PswaAuthorizationRule** polecenia cmdlet dodaje nową regułę autoryzacji do zestawu reguł autoryzacji programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="9196b-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="9196b-113">Należy określić użytkowników, komputerów i punkty końcowe programu Windows PowerShell dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="9196b-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="9196b-114">Można określić użytkowników i komputerów indywidualne konta użytkowników i nazwy komputera lub za pośrednictwem grup.</span><span class="sxs-lookup"><span data-stu-id="9196b-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="9196b-115">Dla komputera, który jest przyłączony do domeny usługi Active Directory polecenie cmdlet używa identyfikator zabezpieczeń (SID) komputera, aby utworzyć regułę.</span><span class="sxs-lookup"><span data-stu-id="9196b-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="9196b-116">Dzięki temu można używać krótkiej nazwy, w pełni kwalifikowaną nazwą domeny (FQDN) lub adres IP **nazwy komputera** pola na stronie logowania.</span><span class="sxs-lookup"><span data-stu-id="9196b-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="9196b-117">Na komputerze, który nie jest przyłączony do domeny usługi Active Directory polecenie cmdlet tworzy regułę przy użyciu nazwy komputera dostarczonego przez administratora.</span><span class="sxs-lookup"><span data-stu-id="9196b-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="9196b-118">Pomyślnie nawiązywać połączeń z tą maszyną, użytkownik końcowy Podaj nazwę komputera dokładnie w brzmieniu podanym w regule.</span><span class="sxs-lookup"><span data-stu-id="9196b-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="9196b-119">W przypadku wielu komputerów o takiej samej nazwie w sieci, krótką nazwę może prowadzić do więcej niż jednego komputera.</span><span class="sxs-lookup"><span data-stu-id="9196b-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="9196b-120">Może to prowadzić do niejednoznaczności podczas nawiązywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="9196b-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="9196b-121">Na przykład, jeśli reguła istnieje na komputerze grupy roboczej o nazwie "*serwer1*" i nowy komputer o nazwie *server1.contoso.com* jest dołączony do sieci, powodzenia weryfikacji przy użyciu reguł autoryzacji i Windows PowerShell Web Access próbuje nawiązać połączenie z komputera o nazwie "*serwer1*".</span><span class="sxs-lookup"><span data-stu-id="9196b-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="9196b-122">Nie gwarantuje, że połączenie jest nawiązywane z określonej grupy roboczej komputera; Próba może wprowadzone w grupie roboczej lub komputerów domeny o nazwie "*serwer1*".</span><span class="sxs-lookup"><span data-stu-id="9196b-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="9196b-123">Aby zmniejszyć niejednoznaczności, zalecane jest, użyj nazwy FQDN dla komputera docelowego, jeśli to możliwe utworzyć regułę autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="9196b-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="9196b-124">Reguły autoryzacji ocenić głównej poświadczenia logowania użytkowników programu Windows PowerShell Web Access, poświadczenia alternatywne (znaleziono drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** sekcji Strona logowania).</span><span class="sxs-lookup"><span data-stu-id="9196b-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="9196b-125">Aby na przykład Zobacz przykład 6.</span><span class="sxs-lookup"><span data-stu-id="9196b-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="9196b-126">Parametry</span><span class="sxs-lookup"><span data-stu-id="9196b-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="9196b-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="9196b-128">Określa nazwę grupy komputerów usług domenowych w usłudze Active Directory (AD DS) lub grupy lokalne, na które ta reguła zezwala na dostęp.</span><span class="sxs-lookup"><span data-stu-id="9196b-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-129">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-129">Aliases</span></span>                              | <span data-ttu-id="9196b-130">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-130">none</span></span>                                 |
| <span data-ttu-id="9196b-131">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-131">Required?</span></span>                            | <span data-ttu-id="9196b-132">true</span><span class="sxs-lookup"><span data-stu-id="9196b-132">true</span></span>                                 |
| <span data-ttu-id="9196b-133">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-133">Position?</span></span>                            | <span data-ttu-id="9196b-134">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9196b-134">named</span></span>                                |
| <span data-ttu-id="9196b-135">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-135">Default Value</span></span>                        | <span data-ttu-id="9196b-136">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-136">none</span></span>                                 |
| <span data-ttu-id="9196b-137">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-138">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9196b-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9196b-139">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-140">false</span><span class="sxs-lookup"><span data-stu-id="9196b-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="9196b-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="9196b-142">Określa nazwę komputera, do którego ta reguła zezwala na dostęp.</span><span class="sxs-lookup"><span data-stu-id="9196b-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-143">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-143">Aliases</span></span>                              | <span data-ttu-id="9196b-144">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-144">none</span></span>                                 |
| <span data-ttu-id="9196b-145">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-145">Required?</span></span>                            | <span data-ttu-id="9196b-146">true</span><span class="sxs-lookup"><span data-stu-id="9196b-146">true</span></span>                                 |
| <span data-ttu-id="9196b-147">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-147">Position?</span></span>                            | <span data-ttu-id="9196b-148">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9196b-148">named</span></span>                                |
| <span data-ttu-id="9196b-149">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-149">Default Value</span></span>                        | <span data-ttu-id="9196b-150">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-150">none</span></span>                                 |
| <span data-ttu-id="9196b-151">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-152">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9196b-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9196b-153">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-154">false</span><span class="sxs-lookup"><span data-stu-id="9196b-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="9196b-155">-ConfigurationName&lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="9196b-156">Określa nazwę konfiguracji sesji programu Windows PowerShell, nazywane również obszaru działania, do którego ta reguła zezwala na dostęp.</span><span class="sxs-lookup"><span data-stu-id="9196b-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-157">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-157">Aliases</span></span>                              | <span data-ttu-id="9196b-158">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-158">none</span></span>                                 |
| <span data-ttu-id="9196b-159">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-159">Required?</span></span>                            | <span data-ttu-id="9196b-160">true</span><span class="sxs-lookup"><span data-stu-id="9196b-160">true</span></span>                                 |
| <span data-ttu-id="9196b-161">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-161">Position?</span></span>                            | <span data-ttu-id="9196b-162">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9196b-162">named</span></span>                                |
| <span data-ttu-id="9196b-163">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-163">Default Value</span></span>                        | <span data-ttu-id="9196b-164">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-164">none</span></span>                                 |
| <span data-ttu-id="9196b-165">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-166">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9196b-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9196b-167">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-168">false</span><span class="sxs-lookup"><span data-stu-id="9196b-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="9196b-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="9196b-170">Określa **PSCredential** obiektu dla konta użytkownika, którego chcesz użyć, aby zmienić reguł autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9196b-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="9196b-171">Jeśli ten parametr nie zostanie użyty, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9196b-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="9196b-172">Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby dodać reguły autoryzacji zdalnie, uruchom [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9196b-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-173">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-173">Aliases</span></span>                              | <span data-ttu-id="9196b-174">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-174">none</span></span>                                 |
| <span data-ttu-id="9196b-175">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-175">Required?</span></span>                            | <span data-ttu-id="9196b-176">false</span><span class="sxs-lookup"><span data-stu-id="9196b-176">false</span></span>                                |
| <span data-ttu-id="9196b-177">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-177">Position?</span></span>                            | <span data-ttu-id="9196b-178">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9196b-178">named</span></span>                                |
| <span data-ttu-id="9196b-179">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-179">Default Value</span></span>                        | <span data-ttu-id="9196b-180">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-180">none</span></span>                                 |
| <span data-ttu-id="9196b-181">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-182">false</span><span class="sxs-lookup"><span data-stu-id="9196b-182">false</span></span>                                |
| <span data-ttu-id="9196b-183">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-184">false</span><span class="sxs-lookup"><span data-stu-id="9196b-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="9196b-185">-Force</span><span class="sxs-lookup"><span data-stu-id="9196b-185">-Force</span></span>

<span data-ttu-id="9196b-186">Wymusza wykonanie polecenia bez monitowania o potwierdzenie przez użytkownika. \\</span><span class="sxs-lookup"><span data-stu-id="9196b-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="9196b-187">Ponadto on również monituje o potwierdzenie po wprowadzeniu nazwy prostej lub krótkiej komputera (takie jak nazwa, która nie jest nazwą domeny lub nie jest w pełni kwalifikowana).</span><span class="sxs-lookup"><span data-stu-id="9196b-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="9196b-188">Potwierdzenie żądania ze względów bezpieczeństwa, aby mogli używać prostą nazwą, aby dodać komputer tylko wtedy, gdy komputer znajduje się w grupie roboczej.</span><span class="sxs-lookup"><span data-stu-id="9196b-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-189">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-189">Aliases</span></span>                              | <span data-ttu-id="9196b-190">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-190">none</span></span>                                 |
| <span data-ttu-id="9196b-191">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-191">Required?</span></span>                            | <span data-ttu-id="9196b-192">false</span><span class="sxs-lookup"><span data-stu-id="9196b-192">false</span></span>                                |
| <span data-ttu-id="9196b-193">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-193">Position?</span></span>                            | <span data-ttu-id="9196b-194">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9196b-194">named</span></span>                                |
| <span data-ttu-id="9196b-195">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-195">Default Value</span></span>                        | <span data-ttu-id="9196b-196">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-196">none</span></span>                                 |
| <span data-ttu-id="9196b-197">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-198">false</span><span class="sxs-lookup"><span data-stu-id="9196b-198">false</span></span>                                |
| <span data-ttu-id="9196b-199">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-200">false</span><span class="sxs-lookup"><span data-stu-id="9196b-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="9196b-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="9196b-202">Określa przyjazną nazwę dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="9196b-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-203">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-203">Aliases</span></span>                              | <span data-ttu-id="9196b-204">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-204">none</span></span>                                 |
| <span data-ttu-id="9196b-205">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-205">Required?</span></span>                            | <span data-ttu-id="9196b-206">false</span><span class="sxs-lookup"><span data-stu-id="9196b-206">false</span></span>                                |
| <span data-ttu-id="9196b-207">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-207">Position?</span></span>                            | <span data-ttu-id="9196b-208">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9196b-208">named</span></span>                                |
| <span data-ttu-id="9196b-209">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-209">Default Value</span></span>                        | <span data-ttu-id="9196b-210">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-210">none</span></span>                                 |
| <span data-ttu-id="9196b-211">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-212">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9196b-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9196b-213">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-214">false</span><span class="sxs-lookup"><span data-stu-id="9196b-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="9196b-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="9196b-216">Określa nazwę jednego lub więcej grup użytkowników w usługach AD DS i grupy lokalne, na które ta reguła zezwala na dostęp.</span><span class="sxs-lookup"><span data-stu-id="9196b-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-217">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-217">Aliases</span></span>                              | <span data-ttu-id="9196b-218">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-218">none</span></span>                                 |
| <span data-ttu-id="9196b-219">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-219">Required?</span></span>                            | <span data-ttu-id="9196b-220">true</span><span class="sxs-lookup"><span data-stu-id="9196b-220">true</span></span>                                 |
| <span data-ttu-id="9196b-221">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-221">Position?</span></span>                            | <span data-ttu-id="9196b-222">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9196b-222">named</span></span>                                |
| <span data-ttu-id="9196b-223">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-223">Default Value</span></span>                        | <span data-ttu-id="9196b-224">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-224">none</span></span>                                 |
| <span data-ttu-id="9196b-225">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-226">Wartość true (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9196b-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="9196b-227">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-228">false</span><span class="sxs-lookup"><span data-stu-id="9196b-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="9196b-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="9196b-230">Określa co najmniej jednego użytkownika, do których ta reguła zezwala na dostęp.</span><span class="sxs-lookup"><span data-stu-id="9196b-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="9196b-231">Nazwa użytkownika może być kontem użytkownika lokalnego na komputerze z bramą lub użytkownika w usługach AD DS.</span><span class="sxs-lookup"><span data-stu-id="9196b-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="9196b-232">Format jest `domain\user` lub `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="9196b-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="9196b-233">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9196b-233">Aliases</span></span>                              | <span data-ttu-id="9196b-234">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-234">none</span></span>                                 |
| <span data-ttu-id="9196b-235">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9196b-235">Required?</span></span>                            | <span data-ttu-id="9196b-236">true</span><span class="sxs-lookup"><span data-stu-id="9196b-236">true</span></span>                                 |
| <span data-ttu-id="9196b-237">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9196b-237">Position?</span></span>                            | <span data-ttu-id="9196b-238">1</span><span class="sxs-lookup"><span data-stu-id="9196b-238">1</span></span>                                    |
| <span data-ttu-id="9196b-239">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9196b-239">Default Value</span></span>                        | <span data-ttu-id="9196b-240">brak</span><span class="sxs-lookup"><span data-stu-id="9196b-240">none</span></span>                                 |
| <span data-ttu-id="9196b-241">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9196b-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9196b-242">Wartość true (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="9196b-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="9196b-243">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9196b-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9196b-244">false</span><span class="sxs-lookup"><span data-stu-id="9196b-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="9196b-245">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="9196b-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="9196b-246">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="9196b-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="9196b-247">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="9196b-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="9196b-248">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="9196b-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="9196b-249">Ciąg</span><span class="sxs-lookup"><span data-stu-id="9196b-249">String</span></span>

<span data-ttu-id="9196b-250">To polecenie cmdlet akceptuje ciągiem lub tablicą ciągów jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9196b-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="9196b-251">Ciąg\[\]</span><span class="sxs-lookup"><span data-stu-id="9196b-251">String\[\]</span></span>

<span data-ttu-id="9196b-252">To polecenie cmdlet akceptuje ciągiem lub tablicą ciągów jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="9196b-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="9196b-253">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="9196b-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="9196b-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9196b-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="9196b-255">To polecenie cmdlet zwraca obiekt reguły autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="9196b-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="9196b-256">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="9196b-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="9196b-257">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="9196b-257">EXAMPLE 1</span></span>

<span data-ttu-id="9196b-258">W tym przykładzie nieograniczony dostęp do konfiguracji sesji *Punktkoncowypswa*, ograniczonym obszarem działania, na *srv2* dla użytkowników w *SMAdmins* grupy. \\</span><span class="sxs-lookup"><span data-stu-id="9196b-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="9196b-259">**Uwaga**: Nazwa komputera musi być w pełni kwalifikowaną nazwą domeny (FQDN).</span><span class="sxs-lookup"><span data-stu-id="9196b-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="9196b-260">Administratorzy zdefiniować konfigurację sesji ograniczony lub obszaru działania, która jest ograniczonym zakresem poleceń cmdlet i zadań, które użytkownicy końcowi mogą uruchamiać.</span><span class="sxs-lookup"><span data-stu-id="9196b-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="9196b-261">Zdefiniowanie ograniczonego obszaru działania może uniemożliwić użytkownikom dostęp do innych komputerów, które są nie w obszarze działania Windows PowerShell® dozwolone, a tym samym zapewnia bardziej bezpiecznego połączenia.</span><span class="sxs-lookup"><span data-stu-id="9196b-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="9196b-262">Aby uzyskać więcej informacji na temat konfiguracji sesji, zobacz [informacje o konfiguracjach sesji](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) lub [instalacji i użyj Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="9196b-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="9196b-263">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="9196b-263">EXAMPLE 2</span></span>

<span data-ttu-id="9196b-264">W tym przykładzie nieograniczony dostęp do domyślnej konfiguracji sesji środowiska Windows PowerShell, `Microsoft.PowerShell`na *srv2* dla użytkowników w użytkowników o nazwie contoso\\Użytkownik1, contoso\\Użytkownik2 i contoso\\UŻYTKOWNIK3.</span><span class="sxs-lookup"><span data-stu-id="9196b-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="9196b-265">To polecenie cmdlet tworzy trzy reguły (1 na osobę).</span><span class="sxs-lookup"><span data-stu-id="9196b-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="9196b-266">PRZYKŁAD 3</span><span class="sxs-lookup"><span data-stu-id="9196b-266">EXAMPLE 3</span></span>

<span data-ttu-id="9196b-267">W tym przykładzie przedstawiono sposób wprowadzania wartości nazwy użytkownika za pośrednictwem potoku.</span><span class="sxs-lookup"><span data-stu-id="9196b-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="9196b-268">PRZYKŁAD 4</span><span class="sxs-lookup"><span data-stu-id="9196b-268">EXAMPLE 4</span></span>

<span data-ttu-id="9196b-269">W tym przykładzie przedstawiono sposób wszystkie parametry przyjmować wartości z potoku według nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="9196b-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="9196b-270">PRZYKŁAD 5</span><span class="sxs-lookup"><span data-stu-id="9196b-270">EXAMPLE 5</span></span>

<span data-ttu-id="9196b-271">W tym przykładzie Dodaje regułę w celu zezwalania użytkownika lokalnego o nazwie *PswaServer\\ChrisLocal* dostęp do serwera o nazwie *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="9196b-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="9196b-272">W tym przykładzie przedstawiono scenariusz, w którym brama jest w grupie roboczej i komputer docelowy znajduje się w domenie.</span><span class="sxs-lookup"><span data-stu-id="9196b-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="9196b-273">Reguła autoryzacji dotyczy użytkowników lokalnych w bramie.</span><span class="sxs-lookup"><span data-stu-id="9196b-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="9196b-274">W witrynie Windows PowerShell Web Access logowania w celu pomyślnego uwierzytelnienia użytkownik musi podać drugi zestaw poświadczeń w **opcjonalne ustawienia połączenia** obszaru.</span><span class="sxs-lookup"><span data-stu-id="9196b-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="9196b-275">Serwer bramy zastosuje ten dodatkowy zestaw poświadczeń do uwierzytelniania użytkownika na komputerze docelowym, a serwer o nazwie *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="9196b-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="9196b-276">PRZYKŁAD 6</span><span class="sxs-lookup"><span data-stu-id="9196b-276">EXAMPLE 6</span></span>

<span data-ttu-id="9196b-277">Ten przykład zezwala wszystkim użytkownikom dostęp do wszystkich punktów końcowych na wszystkich komputerach.</span><span class="sxs-lookup"><span data-stu-id="9196b-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="9196b-278">To zasadniczo wyłączenie reguł autoryzacji. \\</span><span class="sxs-lookup"><span data-stu-id="9196b-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="9196b-279">**Uwaga**: użycie `*` wieloznacznego nie jest zalecane w przypadku istotnych dla zabezpieczeń wdrożeń i tylko powinna być brana pod uwagę dla środowisk testowych lub używać w przypadku wdrożeń, w którym można rozluźnić zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9196b-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="9196b-280">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9196b-280">See Also</span></span>

- <span data-ttu-id="9196b-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9196b-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="9196b-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9196b-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="9196b-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9196b-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="9196b-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="9196b-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="9196b-285">Dodawanie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="9196b-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="9196b-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="9196b-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="9196b-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="9196b-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
