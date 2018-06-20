---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190149"
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="ad401-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ad401-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="ad401-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ad401-104">SYNOPSIS</span></span>

<span data-ttu-id="ad401-105">Sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ad401-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad401-106">SKŁADNIA</span><span class="sxs-lookup"><span data-stu-id="ad401-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="ad401-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="ad401-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="ad401-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="ad401-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="ad401-109">OPIS</span><span class="sxs-lookup"><span data-stu-id="ad401-109">DESCRIPTION</span></span>

<span data-ttu-id="ad401-110">**Test-PswaAuthorizationRule** polecenia cmdlet sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ad401-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="ad401-111">To polecenie cmdlet może również służyć do testowania reguł autoryzacji, aby sprawdzić, czy z określonym żądaniem dostępu użytkowników, komputerów lub punkt końcowy jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="ad401-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="ad401-112">Domyślnie to polecenie cmdlet ocenia wszystkie reguły w pliku autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="ad401-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="ad401-113">Można jednak określić podzbiór reguł do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="ad401-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="ad401-114">To polecenie cmdlet służy do rozwiązywania problemów niepowodzenia uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ad401-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="ad401-115">Parametrami tego polecenia cmdlet odpowiadają polom na stronie logowania programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="ad401-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="ad401-116">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="ad401-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="ad401-117">-ComputerName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="ad401-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="ad401-118">Określa nazwę komputera, aby przetestować.</span><span class="sxs-lookup"><span data-stu-id="ad401-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ad401-119">Aliasy</span><span class="sxs-lookup"><span data-stu-id="ad401-119">Aliases</span></span>                              | <span data-ttu-id="ad401-120">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-120">none</span></span>                                 |
| <span data-ttu-id="ad401-121">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="ad401-121">Required?</span></span>                            | <span data-ttu-id="ad401-122">true</span><span class="sxs-lookup"><span data-stu-id="ad401-122">true</span></span>                                 |
| <span data-ttu-id="ad401-123">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="ad401-123">Position?</span></span>                            | <span data-ttu-id="ad401-124">2</span><span class="sxs-lookup"><span data-stu-id="ad401-124">2</span></span>                                    |
| <span data-ttu-id="ad401-125">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ad401-125">Default Value</span></span>                        | <span data-ttu-id="ad401-126">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-126">none</span></span>                                 |
| <span data-ttu-id="ad401-127">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="ad401-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ad401-128">false</span><span class="sxs-lookup"><span data-stu-id="ad401-128">false</span></span>                                |
| <span data-ttu-id="ad401-129">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="ad401-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ad401-130">false</span><span class="sxs-lookup"><span data-stu-id="ad401-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="ad401-131">-ConfigurationName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="ad401-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="ad401-132">Określa nazwę konfiguracji sesji programu Windows PowerShell, znana także jako punktu końcowego lub obszaru działania, aby przetestować.</span><span class="sxs-lookup"><span data-stu-id="ad401-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ad401-133">Aliasy</span><span class="sxs-lookup"><span data-stu-id="ad401-133">Aliases</span></span>                              | <span data-ttu-id="ad401-134">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-134">none</span></span>                                 |
| <span data-ttu-id="ad401-135">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="ad401-135">Required?</span></span>                            | <span data-ttu-id="ad401-136">false</span><span class="sxs-lookup"><span data-stu-id="ad401-136">false</span></span>                                |
| <span data-ttu-id="ad401-137">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="ad401-137">Position?</span></span>                            | <span data-ttu-id="ad401-138">3</span><span class="sxs-lookup"><span data-stu-id="ad401-138">3</span></span>                                    |
| <span data-ttu-id="ad401-139">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ad401-139">Default Value</span></span>                        | <span data-ttu-id="ad401-140">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-140">none</span></span>                                 |
| <span data-ttu-id="ad401-141">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="ad401-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ad401-142">false</span><span class="sxs-lookup"><span data-stu-id="ad401-142">false</span></span>                                |
| <span data-ttu-id="ad401-143">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="ad401-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ad401-144">false</span><span class="sxs-lookup"><span data-stu-id="ad401-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="ad401-145">-ConnectionUri &lt;identyfikatora Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="ad401-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="ad401-146">Określa identyfikator URI, aby przetestować połączenie.</span><span class="sxs-lookup"><span data-stu-id="ad401-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ad401-147">Aliasy</span><span class="sxs-lookup"><span data-stu-id="ad401-147">Aliases</span></span>                              | <span data-ttu-id="ad401-148">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-148">none</span></span>                                 |
| <span data-ttu-id="ad401-149">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="ad401-149">Required?</span></span>                            | <span data-ttu-id="ad401-150">true</span><span class="sxs-lookup"><span data-stu-id="ad401-150">true</span></span>                                 |
| <span data-ttu-id="ad401-151">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="ad401-151">Position?</span></span>                            | <span data-ttu-id="ad401-152">2</span><span class="sxs-lookup"><span data-stu-id="ad401-152">2</span></span>                                    |
| <span data-ttu-id="ad401-153">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ad401-153">Default Value</span></span>                        | <span data-ttu-id="ad401-154">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-154">none</span></span>                                 |
| <span data-ttu-id="ad401-155">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="ad401-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ad401-156">false</span><span class="sxs-lookup"><span data-stu-id="ad401-156">false</span></span>                                |
| <span data-ttu-id="ad401-157">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="ad401-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ad401-158">false</span><span class="sxs-lookup"><span data-stu-id="ad401-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="ad401-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="ad401-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="ad401-160">Określa **PSCredential** obiektu dla konta użytkownika, którego chcesz używać do testowania reguł autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ad401-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="ad401-161">Jeśli ten parametr nie zostanie użyty, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad401-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="ad401-162">Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby zdalnie testowanie reguł autoryzacji, uruchom [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ad401-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="ad401-163">Aliasy</span><span class="sxs-lookup"><span data-stu-id="ad401-163">Aliases</span></span>                              | <span data-ttu-id="ad401-164">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-164">none</span></span>                                 |
| <span data-ttu-id="ad401-165">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="ad401-165">Required?</span></span>                            | <span data-ttu-id="ad401-166">false</span><span class="sxs-lookup"><span data-stu-id="ad401-166">false</span></span>                                |
| <span data-ttu-id="ad401-167">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="ad401-167">Position?</span></span>                            | <span data-ttu-id="ad401-168">o nazwie</span><span class="sxs-lookup"><span data-stu-id="ad401-168">named</span></span>                                |
| <span data-ttu-id="ad401-169">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ad401-169">Default Value</span></span>                        | <span data-ttu-id="ad401-170">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-170">none</span></span>                                 |
| <span data-ttu-id="ad401-171">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="ad401-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ad401-172">false</span><span class="sxs-lookup"><span data-stu-id="ad401-172">false</span></span>                                |
| <span data-ttu-id="ad401-173">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="ad401-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ad401-174">false</span><span class="sxs-lookup"><span data-stu-id="ad401-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="ad401-175">-Reguły &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="ad401-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="ad401-176">Określa podzbiór reguł do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="ad401-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="ad401-177">Jeśli ten parametr nie jest określony, to polecenie cmdlet testy względem wszystkich reguł autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="ad401-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="ad401-178">Aliasy</span><span class="sxs-lookup"><span data-stu-id="ad401-178">Aliases</span></span>                              | <span data-ttu-id="ad401-179">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-179">none</span></span>                                 |
| <span data-ttu-id="ad401-180">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="ad401-180">Required?</span></span>                            | <span data-ttu-id="ad401-181">false</span><span class="sxs-lookup"><span data-stu-id="ad401-181">false</span></span>                                |
| <span data-ttu-id="ad401-182">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="ad401-182">Position?</span></span>                            | <span data-ttu-id="ad401-183">o nazwie</span><span class="sxs-lookup"><span data-stu-id="ad401-183">named</span></span>                                |
| <span data-ttu-id="ad401-184">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ad401-184">Default Value</span></span>                        | <span data-ttu-id="ad401-185">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-185">none</span></span>                                 |
| <span data-ttu-id="ad401-186">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="ad401-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ad401-187">Wartość true (ByValue)</span><span class="sxs-lookup"><span data-stu-id="ad401-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="ad401-188">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="ad401-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ad401-189">false</span><span class="sxs-lookup"><span data-stu-id="ad401-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="ad401-190">-UserName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="ad401-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="ad401-191">Określa nazwę użytkownika do testowania.</span><span class="sxs-lookup"><span data-stu-id="ad401-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="ad401-192">Aliasy</span><span class="sxs-lookup"><span data-stu-id="ad401-192">Aliases</span></span>                              | <span data-ttu-id="ad401-193">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-193">none</span></span>                                 |
| <span data-ttu-id="ad401-194">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="ad401-194">Required?</span></span>                            | <span data-ttu-id="ad401-195">true</span><span class="sxs-lookup"><span data-stu-id="ad401-195">true</span></span>                                 |
| <span data-ttu-id="ad401-196">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="ad401-196">Position?</span></span>                            | <span data-ttu-id="ad401-197">1</span><span class="sxs-lookup"><span data-stu-id="ad401-197">1</span></span>                                    |
| <span data-ttu-id="ad401-198">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="ad401-198">Default Value</span></span>                        | <span data-ttu-id="ad401-199">brak</span><span class="sxs-lookup"><span data-stu-id="ad401-199">none</span></span>                                 |
| <span data-ttu-id="ad401-200">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="ad401-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ad401-201">false</span><span class="sxs-lookup"><span data-stu-id="ad401-201">false</span></span>                                |
| <span data-ttu-id="ad401-202">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="ad401-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ad401-203">false</span><span class="sxs-lookup"><span data-stu-id="ad401-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="ad401-204">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="ad401-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="ad401-205">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="ad401-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="ad401-206">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ad401-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="ad401-207">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="ad401-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ad401-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ad401-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ad401-209">To polecenie cmdlet akceptuje tablicę obiektów PswaAuthorizationRule jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="ad401-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="ad401-210">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="ad401-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ad401-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ad401-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ad401-212">To polecenie cmdlet tworzy tablicę obiektów PswaAuthorizationRule jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ad401-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="ad401-213">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="ad401-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="ad401-214">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="ad401-214">EXAMPLE 1</span></span>

<span data-ttu-id="ad401-215">W tym przykładzie testów wszystkich reguł autoryzacji, aby wyświetlić wszystkie reguły, które umożliwiają użytkownikowi *contoso\\mhanson* do łączenia się z komputerem *srv2* i użyj sesji programu Windows PowerShell konfigurację o nazwie *testu*.</span><span class="sxs-lookup"><span data-stu-id="ad401-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="ad401-216">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="ad401-216">EXAMPLE 2</span></span>

<span data-ttu-id="ad401-217">Ten testy przykład dotyczą wszystkich reguł autoryzacji, aby sprawdzić, jakie reguły autoryzacji użytkownika *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="ad401-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="ad401-218">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="ad401-218">Related topics</span></span>

- [<span data-ttu-id="ad401-219">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ad401-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="ad401-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ad401-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="ad401-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ad401-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="ad401-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ad401-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)