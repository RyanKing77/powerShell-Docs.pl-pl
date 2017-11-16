---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 2016-12-12
title: "Usuń pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: a8304b68a446de0be98aa732304c71302fb8389e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="af0d4-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="af0d4-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="af0d4-104">STRESZCZENIE</span><span class="sxs-lookup"><span data-stu-id="af0d4-104">SYNOPSIS</span></span>

<span data-ttu-id="af0d4-105">Usuwa wskazaną regułę autoryzacji z programu Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="af0d4-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="af0d4-106">SKŁADNIA</span><span class="sxs-lookup"><span data-stu-id="af0d4-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="af0d4-107">Id</span><span class="sxs-lookup"><span data-stu-id="af0d4-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="af0d4-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="af0d4-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="af0d4-109">OPIS</span><span class="sxs-lookup"><span data-stu-id="af0d4-109">DESCRIPTION</span></span>

<span data-ttu-id="af0d4-110">Usuwa wskazaną regułę autoryzacji z programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="af0d4-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="af0d4-111">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="af0d4-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="af0d4-112">-Force</span><span class="sxs-lookup"><span data-stu-id="af0d4-112">-Force</span></span>

<span data-ttu-id="af0d4-113">Uruchamia polecenie cmdlet bez monitowania o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="af0d4-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="af0d4-114">Domyślnie polecenia cmdlet wyświetlona prośba o potwierdzenie przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="af0d4-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="af0d4-115">Aliasy</span><span class="sxs-lookup"><span data-stu-id="af0d4-115">Aliases</span></span>                              | <span data-ttu-id="af0d4-116">brak</span><span class="sxs-lookup"><span data-stu-id="af0d4-116">none</span></span>                                 |
| <span data-ttu-id="af0d4-117">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="af0d4-117">Required?</span></span>                            | <span data-ttu-id="af0d4-118">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-118">false</span></span>                                |
| <span data-ttu-id="af0d4-119">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="af0d4-119">Position?</span></span>                            | <span data-ttu-id="af0d4-120">o nazwie</span><span class="sxs-lookup"><span data-stu-id="af0d4-120">named</span></span>                                |
| <span data-ttu-id="af0d4-121">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="af0d4-121">Default Value</span></span>                        | <span data-ttu-id="af0d4-122">brak</span><span class="sxs-lookup"><span data-stu-id="af0d4-122">none</span></span>                                 |
| <span data-ttu-id="af0d4-123">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="af0d4-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="af0d4-124">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-124">false</span></span>                                |
| <span data-ttu-id="af0d4-125">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="af0d4-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="af0d4-126">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="af0d4-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="af0d4-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="af0d4-128">Określa identyfikatory (ID) jeden lub więcej reguł do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="af0d4-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="af0d4-129">Aliasy</span><span class="sxs-lookup"><span data-stu-id="af0d4-129">Aliases</span></span>                              | <span data-ttu-id="af0d4-130">brak</span><span class="sxs-lookup"><span data-stu-id="af0d4-130">none</span></span>                                 |
| <span data-ttu-id="af0d4-131">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="af0d4-131">Required?</span></span>                            | <span data-ttu-id="af0d4-132">Wartość true</span><span class="sxs-lookup"><span data-stu-id="af0d4-132">true</span></span>                                 |
| <span data-ttu-id="af0d4-133">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="af0d4-133">Position?</span></span>                            | <span data-ttu-id="af0d4-134">2</span><span class="sxs-lookup"><span data-stu-id="af0d4-134">2</span></span>                                    |
| <span data-ttu-id="af0d4-135">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="af0d4-135">Default Value</span></span>                        | <span data-ttu-id="af0d4-136">brak</span><span class="sxs-lookup"><span data-stu-id="af0d4-136">none</span></span>                                 |
| <span data-ttu-id="af0d4-137">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="af0d4-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="af0d4-138">Wartość true (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="af0d4-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="af0d4-139">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="af0d4-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="af0d4-140">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="af0d4-141">-Reguły &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="af0d4-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="af0d4-142">Określa reguły do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="af0d4-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="af0d4-143">Aliasy</span><span class="sxs-lookup"><span data-stu-id="af0d4-143">Aliases</span></span>                              | <span data-ttu-id="af0d4-144">brak</span><span class="sxs-lookup"><span data-stu-id="af0d4-144">none</span></span>                                 |
| <span data-ttu-id="af0d4-145">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="af0d4-145">Required?</span></span>                            | <span data-ttu-id="af0d4-146">Wartość true</span><span class="sxs-lookup"><span data-stu-id="af0d4-146">true</span></span>                                 |
| <span data-ttu-id="af0d4-147">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="af0d4-147">Position?</span></span>                            | <span data-ttu-id="af0d4-148">2</span><span class="sxs-lookup"><span data-stu-id="af0d4-148">2</span></span>                                    |
| <span data-ttu-id="af0d4-149">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="af0d4-149">Default Value</span></span>                        | <span data-ttu-id="af0d4-150">brak</span><span class="sxs-lookup"><span data-stu-id="af0d4-150">none</span></span>                                 |
| <span data-ttu-id="af0d4-151">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="af0d4-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="af0d4-152">Wartość true (ByValue)</span><span class="sxs-lookup"><span data-stu-id="af0d4-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="af0d4-153">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="af0d4-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="af0d4-154">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="af0d4-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="af0d4-155">-Confirm</span></span>

<span data-ttu-id="af0d4-156">Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="af0d4-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="af0d4-157">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="af0d4-157">Required?</span></span>                            | <span data-ttu-id="af0d4-158">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-158">false</span></span>                                |
| <span data-ttu-id="af0d4-159">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="af0d4-159">Position?</span></span>                            | <span data-ttu-id="af0d4-160">o nazwie</span><span class="sxs-lookup"><span data-stu-id="af0d4-160">named</span></span>                                |
| <span data-ttu-id="af0d4-161">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="af0d4-161">Default Value</span></span>                        | <span data-ttu-id="af0d4-162">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-162">false</span></span>                                |
| <span data-ttu-id="af0d4-163">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="af0d4-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="af0d4-164">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-164">false</span></span>                                |
| <span data-ttu-id="af0d4-165">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="af0d4-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="af0d4-166">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="af0d4-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="af0d4-167">-WhatIf</span></span>

<span data-ttu-id="af0d4-168">Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="af0d4-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="af0d4-169">Polecenie cmdlet nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="af0d4-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="af0d4-170">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="af0d4-170">Required?</span></span>                            | <span data-ttu-id="af0d4-171">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-171">false</span></span>                                |
| <span data-ttu-id="af0d4-172">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="af0d4-172">Position?</span></span>                            | <span data-ttu-id="af0d4-173">o nazwie</span><span class="sxs-lookup"><span data-stu-id="af0d4-173">named</span></span>                                |
| <span data-ttu-id="af0d4-174">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="af0d4-174">Default Value</span></span>                        | <span data-ttu-id="af0d4-175">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-175">false</span></span>                                |
| <span data-ttu-id="af0d4-176">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="af0d4-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="af0d4-177">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-177">false</span></span>                                |
| <span data-ttu-id="af0d4-178">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="af0d4-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="af0d4-179">false</span><span class="sxs-lookup"><span data-stu-id="af0d4-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="af0d4-180">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="af0d4-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="af0d4-181">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="af0d4-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="af0d4-182">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="af0d4-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="af0d4-183">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="af0d4-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="af0d4-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="af0d4-184">int\[\]</span></span>

<span data-ttu-id="af0d4-185">To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablicę obiektów PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="af0d4-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="af0d4-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="af0d4-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="af0d4-187">To polecenie cmdlet akceptuje tablica liczb całkowitych lub tablicę obiektów PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="af0d4-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="af0d4-188">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="af0d4-188">OUTPUTS</span></span>

<span data-ttu-id="af0d4-189">To polecenie cmdlet nie generuje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="af0d4-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="af0d4-190">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="af0d4-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="af0d4-191">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="af0d4-191">EXAMPLE 1</span></span>

<span data-ttu-id="af0d4-192">W tym przykładzie usuwa regułę autoryzacji z Identyfikatorem *2*.</span><span class="sxs-lookup"><span data-stu-id="af0d4-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="af0d4-193">PRZYKŁAD 2 {.subHeading #example-2}</span><span class="sxs-lookup"><span data-stu-id="af0d4-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="af0d4-194">W tym przykładzie powoduje usunięcie wszystkich reguł autoryzacji i wymaga także potwierdzenia przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="af0d4-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="af0d4-195">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="af0d4-195">Related topics</span></span>

- [<span data-ttu-id="af0d4-196">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="af0d4-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="af0d4-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="af0d4-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="af0d4-198">Polecenia cmdlet Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="af0d4-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="af0d4-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="af0d4-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
