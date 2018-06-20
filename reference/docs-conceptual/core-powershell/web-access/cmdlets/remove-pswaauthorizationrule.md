---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189037"
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="388e3-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="388e3-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="388e3-104">STRESZCZENIE</span><span class="sxs-lookup"><span data-stu-id="388e3-104">SYNOPSIS</span></span>

<span data-ttu-id="388e3-105">Usuwa wskazaną regułę autoryzacji z programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="388e3-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="388e3-106">SKŁADNIA</span><span class="sxs-lookup"><span data-stu-id="388e3-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="388e3-107">Id</span><span class="sxs-lookup"><span data-stu-id="388e3-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="388e3-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="388e3-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="388e3-109">OPIS</span><span class="sxs-lookup"><span data-stu-id="388e3-109">DESCRIPTION</span></span>

<span data-ttu-id="388e3-110">Usuwa wskazaną regułę autoryzacji z programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="388e3-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="388e3-111">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="388e3-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="388e3-112">-Force</span><span class="sxs-lookup"><span data-stu-id="388e3-112">-Force</span></span>

<span data-ttu-id="388e3-113">Uruchamia polecenie cmdlet bez monitowania o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="388e3-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="388e3-114">Domyślnie polecenia cmdlet wyświetlona prośba o potwierdzenie przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="388e3-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="388e3-115">Aliasy</span><span class="sxs-lookup"><span data-stu-id="388e3-115">Aliases</span></span>                              | <span data-ttu-id="388e3-116">brak</span><span class="sxs-lookup"><span data-stu-id="388e3-116">none</span></span>                                 |
| <span data-ttu-id="388e3-117">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="388e3-117">Required?</span></span>                            | <span data-ttu-id="388e3-118">false</span><span class="sxs-lookup"><span data-stu-id="388e3-118">false</span></span>                                |
| <span data-ttu-id="388e3-119">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="388e3-119">Position?</span></span>                            | <span data-ttu-id="388e3-120">o nazwie</span><span class="sxs-lookup"><span data-stu-id="388e3-120">named</span></span>                                |
| <span data-ttu-id="388e3-121">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="388e3-121">Default Value</span></span>                        | <span data-ttu-id="388e3-122">brak</span><span class="sxs-lookup"><span data-stu-id="388e3-122">none</span></span>                                 |
| <span data-ttu-id="388e3-123">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="388e3-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="388e3-124">false</span><span class="sxs-lookup"><span data-stu-id="388e3-124">false</span></span>                                |
| <span data-ttu-id="388e3-125">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="388e3-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="388e3-126">false</span><span class="sxs-lookup"><span data-stu-id="388e3-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="388e3-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="388e3-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="388e3-128">Określa identyfikatory (ID) jeden lub więcej reguł do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="388e3-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="388e3-129">Aliasy</span><span class="sxs-lookup"><span data-stu-id="388e3-129">Aliases</span></span>                              | <span data-ttu-id="388e3-130">brak</span><span class="sxs-lookup"><span data-stu-id="388e3-130">none</span></span>                                 |
| <span data-ttu-id="388e3-131">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="388e3-131">Required?</span></span>                            | <span data-ttu-id="388e3-132">true</span><span class="sxs-lookup"><span data-stu-id="388e3-132">true</span></span>                                 |
| <span data-ttu-id="388e3-133">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="388e3-133">Position?</span></span>                            | <span data-ttu-id="388e3-134">2</span><span class="sxs-lookup"><span data-stu-id="388e3-134">2</span></span>                                    |
| <span data-ttu-id="388e3-135">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="388e3-135">Default Value</span></span>                        | <span data-ttu-id="388e3-136">brak</span><span class="sxs-lookup"><span data-stu-id="388e3-136">none</span></span>                                 |
| <span data-ttu-id="388e3-137">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="388e3-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="388e3-138">Wartość true (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="388e3-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="388e3-139">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="388e3-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="388e3-140">false</span><span class="sxs-lookup"><span data-stu-id="388e3-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="388e3-141">-Reguły &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="388e3-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="388e3-142">Określa reguły do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="388e3-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="388e3-143">Aliasy</span><span class="sxs-lookup"><span data-stu-id="388e3-143">Aliases</span></span>                              | <span data-ttu-id="388e3-144">brak</span><span class="sxs-lookup"><span data-stu-id="388e3-144">none</span></span>                                 |
| <span data-ttu-id="388e3-145">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="388e3-145">Required?</span></span>                            | <span data-ttu-id="388e3-146">true</span><span class="sxs-lookup"><span data-stu-id="388e3-146">true</span></span>                                 |
| <span data-ttu-id="388e3-147">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="388e3-147">Position?</span></span>                            | <span data-ttu-id="388e3-148">2</span><span class="sxs-lookup"><span data-stu-id="388e3-148">2</span></span>                                    |
| <span data-ttu-id="388e3-149">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="388e3-149">Default Value</span></span>                        | <span data-ttu-id="388e3-150">brak</span><span class="sxs-lookup"><span data-stu-id="388e3-150">none</span></span>                                 |
| <span data-ttu-id="388e3-151">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="388e3-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="388e3-152">Wartość true (ByValue)</span><span class="sxs-lookup"><span data-stu-id="388e3-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="388e3-153">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="388e3-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="388e3-154">false</span><span class="sxs-lookup"><span data-stu-id="388e3-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="388e3-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="388e3-155">-Confirm</span></span>

<span data-ttu-id="388e3-156">Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="388e3-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="388e3-157">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="388e3-157">Required?</span></span>                            | <span data-ttu-id="388e3-158">false</span><span class="sxs-lookup"><span data-stu-id="388e3-158">false</span></span>                                |
| <span data-ttu-id="388e3-159">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="388e3-159">Position?</span></span>                            | <span data-ttu-id="388e3-160">o nazwie</span><span class="sxs-lookup"><span data-stu-id="388e3-160">named</span></span>                                |
| <span data-ttu-id="388e3-161">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="388e3-161">Default Value</span></span>                        | <span data-ttu-id="388e3-162">false</span><span class="sxs-lookup"><span data-stu-id="388e3-162">false</span></span>                                |
| <span data-ttu-id="388e3-163">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="388e3-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="388e3-164">false</span><span class="sxs-lookup"><span data-stu-id="388e3-164">false</span></span>                                |
| <span data-ttu-id="388e3-165">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="388e3-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="388e3-166">false</span><span class="sxs-lookup"><span data-stu-id="388e3-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="388e3-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="388e3-167">-WhatIf</span></span>

<span data-ttu-id="388e3-168">Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="388e3-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="388e3-169">Polecenie cmdlet nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="388e3-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="388e3-170">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="388e3-170">Required?</span></span>                            | <span data-ttu-id="388e3-171">false</span><span class="sxs-lookup"><span data-stu-id="388e3-171">false</span></span>                                |
| <span data-ttu-id="388e3-172">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="388e3-172">Position?</span></span>                            | <span data-ttu-id="388e3-173">o nazwie</span><span class="sxs-lookup"><span data-stu-id="388e3-173">named</span></span>                                |
| <span data-ttu-id="388e3-174">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="388e3-174">Default Value</span></span>                        | <span data-ttu-id="388e3-175">false</span><span class="sxs-lookup"><span data-stu-id="388e3-175">false</span></span>                                |
| <span data-ttu-id="388e3-176">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="388e3-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="388e3-177">false</span><span class="sxs-lookup"><span data-stu-id="388e3-177">false</span></span>                                |
| <span data-ttu-id="388e3-178">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="388e3-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="388e3-179">false</span><span class="sxs-lookup"><span data-stu-id="388e3-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="388e3-180">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="388e3-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="388e3-181">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="388e3-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="388e3-182">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="388e3-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="388e3-183">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="388e3-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="388e3-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="388e3-184">int\[\]</span></span>

<span data-ttu-id="388e3-185">To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablicę obiektów PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="388e3-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="388e3-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="388e3-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="388e3-187">To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablicę obiektów PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="388e3-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="388e3-188">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="388e3-188">OUTPUTS</span></span>

<span data-ttu-id="388e3-189">To polecenie cmdlet nie generuje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="388e3-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="388e3-190">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="388e3-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="388e3-191">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="388e3-191">EXAMPLE 1</span></span>

<span data-ttu-id="388e3-192">W tym przykładzie usuwa regułę autoryzacji z Identyfikatorem *2*.</span><span class="sxs-lookup"><span data-stu-id="388e3-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="388e3-193">PRZYKŁAD 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="388e3-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="388e3-194">W tym przykładzie powoduje usunięcie wszystkich reguł autoryzacji i wymaga także potwierdzenia przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="388e3-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="388e3-195">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="388e3-195">Related topics</span></span>

- [<span data-ttu-id="388e3-196">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="388e3-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="388e3-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="388e3-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="388e3-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="388e3-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="388e3-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="388e3-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)