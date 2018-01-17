---
description: 
ms.topic: article
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 2016-12-12
title: Test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: fb2937397616160c70b056e412e42fb8ff4c2f27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="63b18-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63b18-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="63b18-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="63b18-104">SYNOPSIS</span></span>

<span data-ttu-id="63b18-105">Sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="63b18-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="63b18-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63b18-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="63b18-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="63b18-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="63b18-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="63b18-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="63b18-109">OPIS</span><span class="sxs-lookup"><span data-stu-id="63b18-109">DESCRIPTION</span></span>

<span data-ttu-id="63b18-110">**Test-PswaAuthorizationRule** polecenia cmdlet sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="63b18-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="63b18-111">To polecenie cmdlet może również służyć do testowania reguł autoryzacji, aby sprawdzić, czy z określonym żądaniem dostępu użytkowników, komputerów lub punkt końcowy jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="63b18-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="63b18-112">Domyślnie to polecenie cmdlet ocenia wszystkie reguły w pliku autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="63b18-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="63b18-113">Można jednak określić podzbiór reguł do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="63b18-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="63b18-114">To polecenie cmdlet służy do rozwiązywania problemów niepowodzenia uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="63b18-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="63b18-115">Parametrami tego polecenia cmdlet odpowiadają polom na stronie logowania programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="63b18-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="63b18-116">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="63b18-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="63b18-117">-ComputerName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="63b18-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="63b18-118">Określa nazwę komputera, aby przetestować.</span><span class="sxs-lookup"><span data-stu-id="63b18-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="63b18-119">Aliasy</span><span class="sxs-lookup"><span data-stu-id="63b18-119">Aliases</span></span>                              | <span data-ttu-id="63b18-120">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-120">none</span></span>                                 |
| <span data-ttu-id="63b18-121">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="63b18-121">Required?</span></span>                            | <span data-ttu-id="63b18-122">true</span><span class="sxs-lookup"><span data-stu-id="63b18-122">true</span></span>                                 |
| <span data-ttu-id="63b18-123">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="63b18-123">Position?</span></span>                            | <span data-ttu-id="63b18-124">2</span><span class="sxs-lookup"><span data-stu-id="63b18-124">2</span></span>                                    |
| <span data-ttu-id="63b18-125">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="63b18-125">Default Value</span></span>                        | <span data-ttu-id="63b18-126">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-126">none</span></span>                                 |
| <span data-ttu-id="63b18-127">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="63b18-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63b18-128">false</span><span class="sxs-lookup"><span data-stu-id="63b18-128">false</span></span>                                |
| <span data-ttu-id="63b18-129">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="63b18-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63b18-130">false</span><span class="sxs-lookup"><span data-stu-id="63b18-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="63b18-131">-ConfigurationName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="63b18-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="63b18-132">Określa nazwę konfiguracji sesji programu Windows PowerShell, znana także jako punktu końcowego lub obszaru działania, aby przetestować.</span><span class="sxs-lookup"><span data-stu-id="63b18-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="63b18-133">Aliasy</span><span class="sxs-lookup"><span data-stu-id="63b18-133">Aliases</span></span>                              | <span data-ttu-id="63b18-134">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-134">none</span></span>                                 |
| <span data-ttu-id="63b18-135">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="63b18-135">Required?</span></span>                            | <span data-ttu-id="63b18-136">false</span><span class="sxs-lookup"><span data-stu-id="63b18-136">false</span></span>                                |
| <span data-ttu-id="63b18-137">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="63b18-137">Position?</span></span>                            | <span data-ttu-id="63b18-138">3</span><span class="sxs-lookup"><span data-stu-id="63b18-138">3</span></span>                                    |
| <span data-ttu-id="63b18-139">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="63b18-139">Default Value</span></span>                        | <span data-ttu-id="63b18-140">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-140">none</span></span>                                 |
| <span data-ttu-id="63b18-141">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="63b18-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63b18-142">false</span><span class="sxs-lookup"><span data-stu-id="63b18-142">false</span></span>                                |
| <span data-ttu-id="63b18-143">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="63b18-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63b18-144">false</span><span class="sxs-lookup"><span data-stu-id="63b18-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="63b18-145">-ConnectionUri &lt;identyfikatora Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="63b18-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="63b18-146">Określa identyfikator URI, aby przetestować połączenie.</span><span class="sxs-lookup"><span data-stu-id="63b18-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="63b18-147">Aliasy</span><span class="sxs-lookup"><span data-stu-id="63b18-147">Aliases</span></span>                              | <span data-ttu-id="63b18-148">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-148">none</span></span>                                 |
| <span data-ttu-id="63b18-149">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="63b18-149">Required?</span></span>                            | <span data-ttu-id="63b18-150">true</span><span class="sxs-lookup"><span data-stu-id="63b18-150">true</span></span>                                 |
| <span data-ttu-id="63b18-151">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="63b18-151">Position?</span></span>                            | <span data-ttu-id="63b18-152">2</span><span class="sxs-lookup"><span data-stu-id="63b18-152">2</span></span>                                    |
| <span data-ttu-id="63b18-153">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="63b18-153">Default Value</span></span>                        | <span data-ttu-id="63b18-154">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-154">none</span></span>                                 |
| <span data-ttu-id="63b18-155">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="63b18-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63b18-156">false</span><span class="sxs-lookup"><span data-stu-id="63b18-156">false</span></span>                                |
| <span data-ttu-id="63b18-157">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="63b18-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63b18-158">false</span><span class="sxs-lookup"><span data-stu-id="63b18-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="63b18-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="63b18-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="63b18-160">Określa **PSCredential** obiektu dla konta użytkownika, którego chcesz używać do testowania reguł autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="63b18-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="63b18-161">Jeśli ten parametr nie zostanie użyty, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="63b18-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="63b18-162">Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby zdalnie testowanie reguł autoryzacji, uruchom [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="63b18-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="63b18-163">Aliasy</span><span class="sxs-lookup"><span data-stu-id="63b18-163">Aliases</span></span>                              | <span data-ttu-id="63b18-164">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-164">none</span></span>                                 |
| <span data-ttu-id="63b18-165">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="63b18-165">Required?</span></span>                            | <span data-ttu-id="63b18-166">false</span><span class="sxs-lookup"><span data-stu-id="63b18-166">false</span></span>                                |
| <span data-ttu-id="63b18-167">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="63b18-167">Position?</span></span>                            | <span data-ttu-id="63b18-168">o nazwie</span><span class="sxs-lookup"><span data-stu-id="63b18-168">named</span></span>                                |
| <span data-ttu-id="63b18-169">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="63b18-169">Default Value</span></span>                        | <span data-ttu-id="63b18-170">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-170">none</span></span>                                 |
| <span data-ttu-id="63b18-171">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="63b18-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63b18-172">false</span><span class="sxs-lookup"><span data-stu-id="63b18-172">false</span></span>                                |
| <span data-ttu-id="63b18-173">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="63b18-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63b18-174">false</span><span class="sxs-lookup"><span data-stu-id="63b18-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="63b18-175">-Reguły &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="63b18-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="63b18-176">Określa podzbiór reguł do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="63b18-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="63b18-177">Jeśli ten parametr nie jest określony, to polecenie cmdlet testy względem wszystkich reguł autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="63b18-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="63b18-178">Aliasy</span><span class="sxs-lookup"><span data-stu-id="63b18-178">Aliases</span></span>                              | <span data-ttu-id="63b18-179">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-179">none</span></span>                                 |
| <span data-ttu-id="63b18-180">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="63b18-180">Required?</span></span>                            | <span data-ttu-id="63b18-181">false</span><span class="sxs-lookup"><span data-stu-id="63b18-181">false</span></span>                                |
| <span data-ttu-id="63b18-182">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="63b18-182">Position?</span></span>                            | <span data-ttu-id="63b18-183">o nazwie</span><span class="sxs-lookup"><span data-stu-id="63b18-183">named</span></span>                                |
| <span data-ttu-id="63b18-184">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="63b18-184">Default Value</span></span>                        | <span data-ttu-id="63b18-185">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-185">none</span></span>                                 |
| <span data-ttu-id="63b18-186">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="63b18-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63b18-187">Wartość true (ByValue)</span><span class="sxs-lookup"><span data-stu-id="63b18-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="63b18-188">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="63b18-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63b18-189">false</span><span class="sxs-lookup"><span data-stu-id="63b18-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="63b18-190">-UserName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="63b18-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="63b18-191">Określa nazwę użytkownika do testowania.</span><span class="sxs-lookup"><span data-stu-id="63b18-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="63b18-192">Aliasy</span><span class="sxs-lookup"><span data-stu-id="63b18-192">Aliases</span></span>                              | <span data-ttu-id="63b18-193">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-193">none</span></span>                                 |
| <span data-ttu-id="63b18-194">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="63b18-194">Required?</span></span>                            | <span data-ttu-id="63b18-195">true</span><span class="sxs-lookup"><span data-stu-id="63b18-195">true</span></span>                                 |
| <span data-ttu-id="63b18-196">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="63b18-196">Position?</span></span>                            | <span data-ttu-id="63b18-197">1</span><span class="sxs-lookup"><span data-stu-id="63b18-197">1</span></span>                                    |
| <span data-ttu-id="63b18-198">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="63b18-198">Default Value</span></span>                        | <span data-ttu-id="63b18-199">brak</span><span class="sxs-lookup"><span data-stu-id="63b18-199">none</span></span>                                 |
| <span data-ttu-id="63b18-200">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="63b18-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="63b18-201">false</span><span class="sxs-lookup"><span data-stu-id="63b18-201">false</span></span>                                |
| <span data-ttu-id="63b18-202">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="63b18-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="63b18-203">false</span><span class="sxs-lookup"><span data-stu-id="63b18-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="63b18-204">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="63b18-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="63b18-205">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="63b18-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="63b18-206">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="63b18-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="63b18-207">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="63b18-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="63b18-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="63b18-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="63b18-209">To polecenie cmdlet akceptuje tablicę obiektów PswaAuthorizationRule jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="63b18-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="63b18-210">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="63b18-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="63b18-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="63b18-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="63b18-212">To polecenie cmdlet tworzy tablicę obiektów PswaAuthorizationRule jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="63b18-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="63b18-213">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="63b18-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="63b18-214">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="63b18-214">EXAMPLE 1</span></span>

<span data-ttu-id="63b18-215">W tym przykładzie testów wszystkich reguł autoryzacji, aby wyświetlić wszystkie reguły, które umożliwiają użytkownikowi *contoso\\mhanson* do łączenia się z komputerem *srv2* i użyj sesji programu Windows PowerShell konfigurację o nazwie *testu*.</span><span class="sxs-lookup"><span data-stu-id="63b18-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="63b18-216">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="63b18-216">EXAMPLE 2</span></span>

<span data-ttu-id="63b18-217">Ten testy przykład dotyczą wszystkich reguł autoryzacji, aby sprawdzić, jakie reguły autoryzacji użytkownika *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="63b18-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="63b18-218">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="63b18-218">Related topics</span></span>

- [<span data-ttu-id="63b18-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63b18-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="63b18-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63b18-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="63b18-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="63b18-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="63b18-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="63b18-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
