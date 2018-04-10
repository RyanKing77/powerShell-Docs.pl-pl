---
description: ''
ms.topic: article
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Odinstaluj pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 139c8358a24e54dec630f8c78737728330ba4aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="e3c4f-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e3c4f-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="e3c4f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e3c4f-104">SYNOPSIS</span></span>

<span data-ttu-id="e3c4f-105">Odinstalowuje Windows PowerShell® aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3c4f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e3c4f-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="e3c4f-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="e3c4f-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="e3c4f-108">OPIS</span><span class="sxs-lookup"><span data-stu-id="e3c4f-108">DESCRIPTION</span></span>

<span data-ttu-id="e3c4f-109">**Uninstall-PswaWebApplication** polecenia cmdlet powoduje odinstalowanie aplikacji sieci web programu Windows PowerShell i usuwa witryny sieci Web usług IIS.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="e3c4f-110">Polecenie cmdlet nie powoduje odinstalowania usług IIS lub innych funkcji zainstalowane, ponieważ są wymagane dla środowiska Windows PowerShell do uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="e3c4f-111">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="e3c4f-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="e3c4f-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="e3c4f-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="e3c4f-113">Wskazuje, że certyfikaty testowe utworzone przez **zainstalować\_PswaWebApplication** polecenia cmdlet (z **UseTestCertificate** parametru) zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="e3c4f-114">Tylko certyfikatu testowego z taką samą nazwę jak utworzony przez **Install-PswaWebApplication** polecenia cmdlet zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="e3c4f-115">Aliasy</span><span class="sxs-lookup"><span data-stu-id="e3c4f-115">Aliases</span></span>                              | <span data-ttu-id="e3c4f-116">brak</span><span class="sxs-lookup"><span data-stu-id="e3c4f-116">none</span></span>                                 |
| <span data-ttu-id="e3c4f-117">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-117">Required?</span></span>                            | <span data-ttu-id="e3c4f-118">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-118">false</span></span>                                |
| <span data-ttu-id="e3c4f-119">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-119">Position?</span></span>                            | <span data-ttu-id="e3c4f-120">o nazwie</span><span class="sxs-lookup"><span data-stu-id="e3c4f-120">named</span></span>                                |
| <span data-ttu-id="e3c4f-121">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="e3c4f-121">Default Value</span></span>                        | <span data-ttu-id="e3c4f-122">true</span><span class="sxs-lookup"><span data-stu-id="e3c4f-122">true</span></span>                                 |
| <span data-ttu-id="e3c4f-123">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e3c4f-124">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-124">false</span></span>                                |
| <span data-ttu-id="e3c4f-125">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e3c4f-126">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="e3c4f-127">-WebApplicationName &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="e3c4f-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="e3c4f-128">Określa nazwę aplikacji sieci web do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="e3c4f-129">Aliasy</span><span class="sxs-lookup"><span data-stu-id="e3c4f-129">Aliases</span></span>                              | <span data-ttu-id="e3c4f-130">brak</span><span class="sxs-lookup"><span data-stu-id="e3c4f-130">none</span></span>                                 |
| <span data-ttu-id="e3c4f-131">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-131">Required?</span></span>                            | <span data-ttu-id="e3c4f-132">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-132">false</span></span>                                |
| <span data-ttu-id="e3c4f-133">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-133">Position?</span></span>                            | <span data-ttu-id="e3c4f-134">1</span><span class="sxs-lookup"><span data-stu-id="e3c4f-134">1</span></span>                                    |
| <span data-ttu-id="e3c4f-135">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="e3c4f-135">Default Value</span></span>                        | <span data-ttu-id="e3c4f-136">pswa</span><span class="sxs-lookup"><span data-stu-id="e3c4f-136">pswa</span></span>                                 |
| <span data-ttu-id="e3c4f-137">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e3c4f-138">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-138">false</span></span>                                |
| <span data-ttu-id="e3c4f-139">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e3c4f-140">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="e3c4f-141">-Podaną &lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="e3c4f-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="e3c4f-142">Określa nazwę witryny sieci web, w którym zainstalowano aplikację sieci web.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="e3c4f-143">Aliasy</span><span class="sxs-lookup"><span data-stu-id="e3c4f-143">Aliases</span></span>                              | <span data-ttu-id="e3c4f-144">brak</span><span class="sxs-lookup"><span data-stu-id="e3c4f-144">none</span></span>                                 |
| <span data-ttu-id="e3c4f-145">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-145">Required?</span></span>                            | <span data-ttu-id="e3c4f-146">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-146">false</span></span>                                |
| <span data-ttu-id="e3c4f-147">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-147">Position?</span></span>                            | <span data-ttu-id="e3c4f-148">o nazwie</span><span class="sxs-lookup"><span data-stu-id="e3c4f-148">named</span></span>                                |
| <span data-ttu-id="e3c4f-149">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="e3c4f-149">Default Value</span></span>                        | <span data-ttu-id="e3c4f-150">Domyślna witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="e3c4f-150">Default Web Site</span></span>                     |
| <span data-ttu-id="e3c4f-151">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e3c4f-152">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-152">false</span></span>                                |
| <span data-ttu-id="e3c4f-153">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e3c4f-154">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="e3c4f-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e3c4f-155">-Confirm</span></span>

<span data-ttu-id="e3c4f-156">Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="e3c4f-157">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-157">Required?</span></span>                            | <span data-ttu-id="e3c4f-158">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-158">false</span></span>                                |
| <span data-ttu-id="e3c4f-159">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-159">Position?</span></span>                            | <span data-ttu-id="e3c4f-160">o nazwie</span><span class="sxs-lookup"><span data-stu-id="e3c4f-160">named</span></span>                                |
| <span data-ttu-id="e3c4f-161">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="e3c4f-161">Default Value</span></span>                        | <span data-ttu-id="e3c4f-162">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-162">false</span></span>                                |
| <span data-ttu-id="e3c4f-163">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e3c4f-164">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-164">false</span></span>                                |
| <span data-ttu-id="e3c4f-165">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e3c4f-166">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="e3c4f-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e3c4f-167">-WhatIf</span></span>

<span data-ttu-id="e3c4f-168">Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e3c4f-169">Polecenie cmdlet nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="e3c4f-170">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-170">Required?</span></span>                            | <span data-ttu-id="e3c4f-171">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-171">false</span></span>                                |
| <span data-ttu-id="e3c4f-172">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-172">Position?</span></span>                            | <span data-ttu-id="e3c4f-173">o nazwie</span><span class="sxs-lookup"><span data-stu-id="e3c4f-173">named</span></span>                                |
| <span data-ttu-id="e3c4f-174">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="e3c4f-174">Default Value</span></span>                        | <span data-ttu-id="e3c4f-175">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-175">false</span></span>                                |
| <span data-ttu-id="e3c4f-176">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e3c4f-177">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-177">false</span></span>                                |
| <span data-ttu-id="e3c4f-178">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="e3c4f-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e3c4f-179">false</span><span class="sxs-lookup"><span data-stu-id="e3c4f-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="e3c4f-180">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="e3c4f-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="e3c4f-181">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="e3c4f-182">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e3c4f-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="e3c4f-183">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="e3c4f-183">INPUTS</span></span>

<span data-ttu-id="e3c4f-184">To polecenie cmdlet nie wymaga danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="e3c4f-185">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="e3c4f-185">OUTPUTS</span></span>

<span data-ttu-id="e3c4f-186">To polecenie cmdlet nie zwraca żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="e3c4f-187">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="e3c4f-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="e3c4f-188">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="e3c4f-188">EXAMPLE 1</span></span>

<span data-ttu-id="e3c4f-189">To polecenie spowoduje odinstalowanie aplikacji sieci Web programu Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="e3c4f-190">To polecenie cmdlet służy do odinstalowania aplikacji sieci Web programu Windows PowerShell, jeśli został zainstalowany przy użyciu wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="e3c4f-191">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="e3c4f-191">EXAMPLE 2</span></span>

<span data-ttu-id="e3c4f-192">To polecenie powoduje odinstalowanie aplikacji sieci Web programu Windows PowerShell i usuwa certyfikatu testowego skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="e3c4f-193">To polecenie cmdlet służy do odinstalowania aplikacji sieci Web programu Windows PowerShell, jeśli po zainstalowaniu go przy użyciu wartości domyślnych utworzony certyfikat testowy.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="e3c4f-194">PRZYKŁAD 3 {.subHeading #example-3}</span><span class="sxs-lookup"><span data-stu-id="e3c4f-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="e3c4f-195">To polecenie spowoduje odinstalowanie aplikacji sieci Web programu Windows PowerShell po niestandardowej witryny sieci Web i aplikacji, które zostały określone podczas instalacji.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="e3c4f-196">Polecenie usuwa witryny sieci Web o nazwie *witryna* i aplikację o nazwie *kategorii Aplikacja_testowa* i Określa certyfikaty testu skojarzone z aplikacją również zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="e3c4f-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="e3c4f-197">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="e3c4f-197">Related topics</span></span>

- [<span data-ttu-id="e3c4f-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e3c4f-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="e3c4f-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e3c4f-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="e3c4f-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e3c4f-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="e3c4f-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e3c4f-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="e3c4f-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e3c4f-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)