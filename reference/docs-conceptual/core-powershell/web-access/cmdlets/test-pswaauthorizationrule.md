---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 2016-12-12
title: Test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="4ae5e-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ae5e-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="4ae5e-104">STRESZCZENIE</span><span class="sxs-lookup"><span data-stu-id="4ae5e-104">SYNOPSIS</span></span>

<span data-ttu-id="4ae5e-105">Sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ae5e-106">SKŁADNIA</span><span class="sxs-lookup"><span data-stu-id="4ae5e-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="4ae5e-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4ae5e-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="4ae5e-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="4ae5e-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4ae5e-109">OPIS</span><span class="sxs-lookup"><span data-stu-id="4ae5e-109">DESCRIPTION</span></span>

<span data-ttu-id="4ae5e-110">**Test-PswaAuthorizationRule** polecenia cmdlet sprawdza, czy reguła istnieje dla określonego użytkownika, komputera lub punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="4ae5e-111">To polecenie cmdlet może również służyć do testowania reguł autoryzacji, aby sprawdzić, czy z określonym żądaniem dostępu użytkowników, komputerów lub punkt końcowy jest autoryzowany.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="4ae5e-112">Domyślnie to polecenie cmdlet ocenia wszystkie reguły w pliku autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="4ae5e-113">Można jednak określić podzbiór reguł do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="4ae5e-114">To polecenie cmdlet służy do rozwiązywania problemów niepowodzenia uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="4ae5e-115">Parametrami tego polecenia cmdlet odpowiadają polom na stronie logowania programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="4ae5e-116">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="4ae5e-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="4ae5e-117">-ComputerName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="4ae5e-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="4ae5e-118">Określa nazwę komputera, aby przetestować.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ae5e-119">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4ae5e-119">Aliases</span></span>                              | <span data-ttu-id="4ae5e-120">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-120">none</span></span>                                 |
| <span data-ttu-id="4ae5e-121">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-121">Required?</span></span>                            | <span data-ttu-id="4ae5e-122">Wartość true</span><span class="sxs-lookup"><span data-stu-id="4ae5e-122">true</span></span>                                 |
| <span data-ttu-id="4ae5e-123">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-123">Position?</span></span>                            | <span data-ttu-id="4ae5e-124">2</span><span class="sxs-lookup"><span data-stu-id="4ae5e-124">2</span></span>                                    |
| <span data-ttu-id="4ae5e-125">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4ae5e-125">Default Value</span></span>                        | <span data-ttu-id="4ae5e-126">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-126">none</span></span>                                 |
| <span data-ttu-id="4ae5e-127">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ae5e-128">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-128">false</span></span>                                |
| <span data-ttu-id="4ae5e-129">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ae5e-130">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="4ae5e-131">-ConfigurationName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="4ae5e-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="4ae5e-132">Określa nazwę konfiguracji sesji programu Windows PowerShell, znana także jako punktu końcowego lub obszaru działania, aby przetestować.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ae5e-133">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4ae5e-133">Aliases</span></span>                              | <span data-ttu-id="4ae5e-134">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-134">none</span></span>                                 |
| <span data-ttu-id="4ae5e-135">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-135">Required?</span></span>                            | <span data-ttu-id="4ae5e-136">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-136">false</span></span>                                |
| <span data-ttu-id="4ae5e-137">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-137">Position?</span></span>                            | <span data-ttu-id="4ae5e-138">3</span><span class="sxs-lookup"><span data-stu-id="4ae5e-138">3</span></span>                                    |
| <span data-ttu-id="4ae5e-139">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4ae5e-139">Default Value</span></span>                        | <span data-ttu-id="4ae5e-140">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-140">none</span></span>                                 |
| <span data-ttu-id="4ae5e-141">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ae5e-142">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-142">false</span></span>                                |
| <span data-ttu-id="4ae5e-143">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ae5e-144">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="4ae5e-145">-ConnectionUri &lt;identyfikatora Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="4ae5e-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="4ae5e-146">Określa identyfikator URI, aby przetestować połączenie.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ae5e-147">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4ae5e-147">Aliases</span></span>                              | <span data-ttu-id="4ae5e-148">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-148">none</span></span>                                 |
| <span data-ttu-id="4ae5e-149">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-149">Required?</span></span>                            | <span data-ttu-id="4ae5e-150">Wartość true</span><span class="sxs-lookup"><span data-stu-id="4ae5e-150">true</span></span>                                 |
| <span data-ttu-id="4ae5e-151">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-151">Position?</span></span>                            | <span data-ttu-id="4ae5e-152">2</span><span class="sxs-lookup"><span data-stu-id="4ae5e-152">2</span></span>                                    |
| <span data-ttu-id="4ae5e-153">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4ae5e-153">Default Value</span></span>                        | <span data-ttu-id="4ae5e-154">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-154">none</span></span>                                 |
| <span data-ttu-id="4ae5e-155">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ae5e-156">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-156">false</span></span>                                |
| <span data-ttu-id="4ae5e-157">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ae5e-158">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="4ae5e-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="4ae5e-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="4ae5e-160">Określa **PSCredential** obiektu dla konta użytkownika, którego chcesz używać do testowania reguł autoryzacji programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="4ae5e-161">Jeśli ten parametr nie zostanie użyty, polecenie cmdlet używa konta aktualnie zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="4ae5e-162">Aby uzyskać **PSCredential** obiektu, który jest wymagany, aby zdalnie testowanie reguł autoryzacji, uruchom [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ae5e-163">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4ae5e-163">Aliases</span></span>                              | <span data-ttu-id="4ae5e-164">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-164">none</span></span>                                 |
| <span data-ttu-id="4ae5e-165">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-165">Required?</span></span>                            | <span data-ttu-id="4ae5e-166">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-166">false</span></span>                                |
| <span data-ttu-id="4ae5e-167">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-167">Position?</span></span>                            | <span data-ttu-id="4ae5e-168">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4ae5e-168">named</span></span>                                |
| <span data-ttu-id="4ae5e-169">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4ae5e-169">Default Value</span></span>                        | <span data-ttu-id="4ae5e-170">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-170">none</span></span>                                 |
| <span data-ttu-id="4ae5e-171">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ae5e-172">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-172">false</span></span>                                |
| <span data-ttu-id="4ae5e-173">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ae5e-174">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="4ae5e-175">-Reguły &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4ae5e-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="4ae5e-176">Określa podzbiór reguł do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="4ae5e-177">Jeśli ten parametr nie jest określony, to polecenie cmdlet testy względem wszystkich reguł autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ae5e-178">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4ae5e-178">Aliases</span></span>                              | <span data-ttu-id="4ae5e-179">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-179">none</span></span>                                 |
| <span data-ttu-id="4ae5e-180">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-180">Required?</span></span>                            | <span data-ttu-id="4ae5e-181">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-181">false</span></span>                                |
| <span data-ttu-id="4ae5e-182">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-182">Position?</span></span>                            | <span data-ttu-id="4ae5e-183">o nazwie</span><span class="sxs-lookup"><span data-stu-id="4ae5e-183">named</span></span>                                |
| <span data-ttu-id="4ae5e-184">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4ae5e-184">Default Value</span></span>                        | <span data-ttu-id="4ae5e-185">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-185">none</span></span>                                 |
| <span data-ttu-id="4ae5e-186">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ae5e-187">Wartość true (ByValue)</span><span class="sxs-lookup"><span data-stu-id="4ae5e-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="4ae5e-188">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ae5e-189">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="4ae5e-190">-UserName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="4ae5e-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="4ae5e-191">Określa nazwę użytkownika do testowania.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4ae5e-192">Aliasy</span><span class="sxs-lookup"><span data-stu-id="4ae5e-192">Aliases</span></span>                              | <span data-ttu-id="4ae5e-193">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-193">none</span></span>                                 |
| <span data-ttu-id="4ae5e-194">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-194">Required?</span></span>                            | <span data-ttu-id="4ae5e-195">Wartość true</span><span class="sxs-lookup"><span data-stu-id="4ae5e-195">true</span></span>                                 |
| <span data-ttu-id="4ae5e-196">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-196">Position?</span></span>                            | <span data-ttu-id="4ae5e-197">1</span><span class="sxs-lookup"><span data-stu-id="4ae5e-197">1</span></span>                                    |
| <span data-ttu-id="4ae5e-198">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="4ae5e-198">Default Value</span></span>                        | <span data-ttu-id="4ae5e-199">brak</span><span class="sxs-lookup"><span data-stu-id="4ae5e-199">none</span></span>                                 |
| <span data-ttu-id="4ae5e-200">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4ae5e-201">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-201">false</span></span>                                |
| <span data-ttu-id="4ae5e-202">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="4ae5e-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4ae5e-203">false</span><span class="sxs-lookup"><span data-stu-id="4ae5e-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4ae5e-204">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="4ae5e-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4ae5e-205">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4ae5e-206">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4ae5e-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4ae5e-207">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="4ae5e-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4ae5e-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4ae5e-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4ae5e-209">To polecenie cmdlet akceptuje tablicę obiektów PswaAuthorizationRule jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4ae5e-210">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="4ae5e-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4ae5e-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4ae5e-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4ae5e-212">To polecenie cmdlet tworzy tablicę obiektów PswaAuthorizationRule jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="4ae5e-213">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="4ae5e-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4ae5e-214">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="4ae5e-214">EXAMPLE 1</span></span>

<span data-ttu-id="4ae5e-215">W tym przykładzie testów wszystkich reguł autoryzacji, aby wyświetlić wszystkie reguły, które umożliwiają użytkownikowi *contoso\\mhanson* do łączenia się z komputerem *srv2* i użyj sesji programu Windows PowerShell konfigurację o nazwie *testu*.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="4ae5e-216">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="4ae5e-216">EXAMPLE 2</span></span>

<span data-ttu-id="4ae5e-217">Ten testy przykład dotyczą wszystkich reguł autoryzacji, aby sprawdzić, jakie reguły autoryzacji użytkownika *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="4ae5e-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="4ae5e-218">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="4ae5e-218">Related topics</span></span>

- [<span data-ttu-id="4ae5e-219">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ae5e-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4ae5e-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ae5e-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="4ae5e-221">Polecenia cmdlet Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4ae5e-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="4ae5e-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4ae5e-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
