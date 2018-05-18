---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="57652-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="57652-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="57652-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="57652-104">SYNOPSIS</span></span>

<span data-ttu-id="57652-105">Konfiguruje aplikację sieci web programu Windows PowerShell® Web Access w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="57652-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="57652-106">SKŁADNIA</span><span class="sxs-lookup"><span data-stu-id="57652-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="57652-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="57652-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="57652-108">OPIS</span><span class="sxs-lookup"><span data-stu-id="57652-108">DESCRIPTION</span></span>

<span data-ttu-id="57652-109">**Install-PswaWebApplication** polecenia cmdlet konfiguruje aplikację sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="57652-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="57652-110">To polecenie cmdlet instaluje aplikację sieci web, kojarzy go z witryny sieci web i opcjonalnie tworzy, używając certyfikatu SSL testu **useTestCertificate** parametru.</span><span class="sxs-lookup"><span data-stu-id="57652-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="57652-111">Dla bezpieczeństwa przyczyny Administratorzy sieci web nie należy używać certyfikatu testowego dla środowisk produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="57652-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="57652-112">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="57652-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="57652-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="57652-113">-UseTestCertificate</span></span>

<span data-ttu-id="57652-114">Określa, czy certyfikat testowy został utworzony.</span><span class="sxs-lookup"><span data-stu-id="57652-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="57652-115">Jeśli ten parametr ma ustawioną wartość PRAWDA, to polecenie cmdlet tworzy certyfikat testowy i konfiguruje aplikację sieci web programu Windows PowerShell Web Access do używania certyfikatu dla żądania HTTPS.</span><span class="sxs-lookup"><span data-stu-id="57652-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="57652-116">Jeśli ten parametr ma wartość false, następnie nie certyfikatu powiązania jest utworzone lub.</span><span class="sxs-lookup"><span data-stu-id="57652-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="57652-117">Wartość tę należy ustawić na wartość false, jeśli inny certyfikat jest używany dla programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="57652-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="57652-118">Aliasy</span><span class="sxs-lookup"><span data-stu-id="57652-118">Aliases</span></span>                              | <span data-ttu-id="57652-119">brak</span><span class="sxs-lookup"><span data-stu-id="57652-119">none</span></span>                                 |
| <span data-ttu-id="57652-120">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="57652-120">Required?</span></span>                            | <span data-ttu-id="57652-121">false</span><span class="sxs-lookup"><span data-stu-id="57652-121">false</span></span>                                |
| <span data-ttu-id="57652-122">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="57652-122">Position?</span></span>                            | <span data-ttu-id="57652-123">o nazwie</span><span class="sxs-lookup"><span data-stu-id="57652-123">named</span></span>                                |
| <span data-ttu-id="57652-124">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="57652-124">Default Value</span></span>                        | <span data-ttu-id="57652-125">true</span><span class="sxs-lookup"><span data-stu-id="57652-125">true</span></span>                                 |
| <span data-ttu-id="57652-126">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="57652-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="57652-127">false</span><span class="sxs-lookup"><span data-stu-id="57652-127">false</span></span>                                |
| <span data-ttu-id="57652-128">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="57652-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="57652-129">false</span><span class="sxs-lookup"><span data-stu-id="57652-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="57652-130">-WebApplicationName&lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="57652-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="57652-131">Określa nazwę aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="57652-131">Specifies the name for your web application.</span></span> <span data-ttu-id="57652-132">Jest on wyświetlany jako ostatnia część adres URL programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="57652-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="57652-133">Aliasy</span><span class="sxs-lookup"><span data-stu-id="57652-133">Aliases</span></span>                              | <span data-ttu-id="57652-134">brak</span><span class="sxs-lookup"><span data-stu-id="57652-134">none</span></span>                                 |
| <span data-ttu-id="57652-135">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="57652-135">Required?</span></span>                            | <span data-ttu-id="57652-136">false</span><span class="sxs-lookup"><span data-stu-id="57652-136">false</span></span>                                |
| <span data-ttu-id="57652-137">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="57652-137">Position?</span></span>                            | <span data-ttu-id="57652-138">1</span><span class="sxs-lookup"><span data-stu-id="57652-138">1</span></span>                                    |
| <span data-ttu-id="57652-139">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="57652-139">Default Value</span></span>                        | <span data-ttu-id="57652-140">pswa</span><span class="sxs-lookup"><span data-stu-id="57652-140">pswa</span></span>                                 |
| <span data-ttu-id="57652-141">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="57652-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="57652-142">false</span><span class="sxs-lookup"><span data-stu-id="57652-142">false</span></span>                                |
| <span data-ttu-id="57652-143">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="57652-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="57652-144">false</span><span class="sxs-lookup"><span data-stu-id="57652-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="57652-145">-Podaną&lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="57652-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="57652-146">Określa nazwę witryny sieci Web serwer sieci Web (IIS), na których chcesz zainstalować tę aplikację sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="57652-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="57652-147">Aliasy</span><span class="sxs-lookup"><span data-stu-id="57652-147">Aliases</span></span>                              | <span data-ttu-id="57652-148">brak</span><span class="sxs-lookup"><span data-stu-id="57652-148">none</span></span>                                 |
| <span data-ttu-id="57652-149">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="57652-149">Required?</span></span>                            | <span data-ttu-id="57652-150">false</span><span class="sxs-lookup"><span data-stu-id="57652-150">false</span></span>                                |
| <span data-ttu-id="57652-151">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="57652-151">Position?</span></span>                            | <span data-ttu-id="57652-152">o nazwie</span><span class="sxs-lookup"><span data-stu-id="57652-152">named</span></span>                                |
| <span data-ttu-id="57652-153">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="57652-153">Default Value</span></span>                        | <span data-ttu-id="57652-154">Domyślna witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="57652-154">Default Web Site</span></span>                     |
| <span data-ttu-id="57652-155">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="57652-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="57652-156">false</span><span class="sxs-lookup"><span data-stu-id="57652-156">false</span></span>                                |
| <span data-ttu-id="57652-157">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="57652-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="57652-158">false</span><span class="sxs-lookup"><span data-stu-id="57652-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="57652-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="57652-159">-Confirm</span></span>

<span data-ttu-id="57652-160">Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57652-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="57652-161">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="57652-161">Required?</span></span>                            | <span data-ttu-id="57652-162">false</span><span class="sxs-lookup"><span data-stu-id="57652-162">false</span></span>                                |
| <span data-ttu-id="57652-163">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="57652-163">Position?</span></span>                            | <span data-ttu-id="57652-164">o nazwie</span><span class="sxs-lookup"><span data-stu-id="57652-164">named</span></span>                                |
| <span data-ttu-id="57652-165">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="57652-165">Default Value</span></span>                        | <span data-ttu-id="57652-166">false</span><span class="sxs-lookup"><span data-stu-id="57652-166">false</span></span>                                |
| <span data-ttu-id="57652-167">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="57652-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="57652-168">false</span><span class="sxs-lookup"><span data-stu-id="57652-168">false</span></span>                                |
| <span data-ttu-id="57652-169">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="57652-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="57652-170">false</span><span class="sxs-lookup"><span data-stu-id="57652-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="57652-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="57652-171">-WhatIf</span></span>

<span data-ttu-id="57652-172">Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57652-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="57652-173">Polecenie cmdlet nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="57652-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="57652-174">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="57652-174">Required?</span></span>                            | <span data-ttu-id="57652-175">false</span><span class="sxs-lookup"><span data-stu-id="57652-175">false</span></span>                                |
| <span data-ttu-id="57652-176">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="57652-176">Position?</span></span>                            | <span data-ttu-id="57652-177">o nazwie</span><span class="sxs-lookup"><span data-stu-id="57652-177">named</span></span>                                |
| <span data-ttu-id="57652-178">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="57652-178">Default Value</span></span>                        | <span data-ttu-id="57652-179">false</span><span class="sxs-lookup"><span data-stu-id="57652-179">false</span></span>                                |
| <span data-ttu-id="57652-180">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="57652-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="57652-181">false</span><span class="sxs-lookup"><span data-stu-id="57652-181">false</span></span>                                |
| <span data-ttu-id="57652-182">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="57652-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="57652-183">false</span><span class="sxs-lookup"><span data-stu-id="57652-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="57652-184">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="57652-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="57652-185">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="57652-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="57652-186">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="57652-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="57652-187">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="57652-187">INPUTS</span></span>

<span data-ttu-id="57652-188">To polecenie cmdlet nie wymaga danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="57652-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="57652-189">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="57652-189">OUTPUTS</span></span>

<span data-ttu-id="57652-190">To polecenie cmdlet nie generuje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="57652-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="57652-191">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="57652-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="57652-192">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="57652-192">EXAMPLE 1</span></span>

<span data-ttu-id="57652-193">Instalacja przy użyciu wartości domyślnych dla aplikacji sieci web PSWA **WebApplicationName** (*pswa*) i **podaną** (*domyślnej witryny sieci Web* ) parametrów.</span><span class="sxs-lookup"><span data-stu-id="57652-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="57652-194">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="57652-194">EXAMPLE 2</span></span>

<span data-ttu-id="57652-195">Instalacja aplikacji sieci web PSWA z certyfikatu testowego i przy użyciu wartości domyślnych **WebApplicationName** i **podaną** parametrów.</span><span class="sxs-lookup"><span data-stu-id="57652-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="57652-196">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="57652-196">Related topics</span></span>

- [<span data-ttu-id="57652-197">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="57652-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="57652-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="57652-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="57652-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="57652-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="57652-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="57652-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)