---
description: ''
ms.topic: article
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Zainstaluj pswawebapplication
ms.technology: powershell
ms.openlocfilehash: c7f7768a41b6784d8c29afa1fccf0b855160b777
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="70d35-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="70d35-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="70d35-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="70d35-104">SYNOPSIS</span></span>

<span data-ttu-id="70d35-105">Konfiguruje aplikację sieci web programu Windows PowerShell® Web Access w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="70d35-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="70d35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="70d35-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="70d35-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="70d35-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="70d35-108">OPIS</span><span class="sxs-lookup"><span data-stu-id="70d35-108">DESCRIPTION</span></span>

<span data-ttu-id="70d35-109">**Install-PswaWebApplication** polecenia cmdlet konfiguruje aplikację sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="70d35-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="70d35-110">To polecenie cmdlet instaluje aplikację sieci web, kojarzy go z witryny sieci web i opcjonalnie tworzy, używając certyfikatu SSL testu **useTestCertificate** parametru.</span><span class="sxs-lookup"><span data-stu-id="70d35-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="70d35-111">Dla bezpieczeństwa przyczyny Administratorzy sieci web nie należy używać certyfikatu testowego dla środowisk produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="70d35-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="70d35-112">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="70d35-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="70d35-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="70d35-113">-UseTestCertificate</span></span>

<span data-ttu-id="70d35-114">Określa, czy certyfikat testowy został utworzony.</span><span class="sxs-lookup"><span data-stu-id="70d35-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="70d35-115">Jeśli ten parametr ma ustawioną wartość PRAWDA, to polecenie cmdlet tworzy certyfikat testowy i konfiguruje aplikację sieci web programu Windows PowerShell Web Access do używania certyfikatu dla żądania HTTPS.</span><span class="sxs-lookup"><span data-stu-id="70d35-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="70d35-116">Jeśli ten parametr ma wartość false, następnie nie certyfikatu powiązania jest utworzone lub.</span><span class="sxs-lookup"><span data-stu-id="70d35-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="70d35-117">Wartość tę należy ustawić na wartość false, jeśli inny certyfikat jest używany dla programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="70d35-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="70d35-118">Aliasy</span><span class="sxs-lookup"><span data-stu-id="70d35-118">Aliases</span></span>                              | <span data-ttu-id="70d35-119">brak</span><span class="sxs-lookup"><span data-stu-id="70d35-119">none</span></span>                                 |
| <span data-ttu-id="70d35-120">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="70d35-120">Required?</span></span>                            | <span data-ttu-id="70d35-121">false</span><span class="sxs-lookup"><span data-stu-id="70d35-121">false</span></span>                                |
| <span data-ttu-id="70d35-122">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="70d35-122">Position?</span></span>                            | <span data-ttu-id="70d35-123">o nazwie</span><span class="sxs-lookup"><span data-stu-id="70d35-123">named</span></span>                                |
| <span data-ttu-id="70d35-124">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="70d35-124">Default Value</span></span>                        | <span data-ttu-id="70d35-125">true</span><span class="sxs-lookup"><span data-stu-id="70d35-125">true</span></span>                                 |
| <span data-ttu-id="70d35-126">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="70d35-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="70d35-127">false</span><span class="sxs-lookup"><span data-stu-id="70d35-127">false</span></span>                                |
| <span data-ttu-id="70d35-128">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="70d35-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="70d35-129">false</span><span class="sxs-lookup"><span data-stu-id="70d35-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="70d35-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="70d35-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="70d35-131">Określa nazwę aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="70d35-131">Specifies the name for your web application.</span></span> <span data-ttu-id="70d35-132">Jest on wyświetlany jako ostatnia część adres URL programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="70d35-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="70d35-133">Aliasy</span><span class="sxs-lookup"><span data-stu-id="70d35-133">Aliases</span></span>                              | <span data-ttu-id="70d35-134">brak</span><span class="sxs-lookup"><span data-stu-id="70d35-134">none</span></span>                                 |
| <span data-ttu-id="70d35-135">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="70d35-135">Required?</span></span>                            | <span data-ttu-id="70d35-136">false</span><span class="sxs-lookup"><span data-stu-id="70d35-136">false</span></span>                                |
| <span data-ttu-id="70d35-137">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="70d35-137">Position?</span></span>                            | <span data-ttu-id="70d35-138">1</span><span class="sxs-lookup"><span data-stu-id="70d35-138">1</span></span>                                    |
| <span data-ttu-id="70d35-139">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="70d35-139">Default Value</span></span>                        | <span data-ttu-id="70d35-140">pswa</span><span class="sxs-lookup"><span data-stu-id="70d35-140">pswa</span></span>                                 |
| <span data-ttu-id="70d35-141">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="70d35-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="70d35-142">false</span><span class="sxs-lookup"><span data-stu-id="70d35-142">false</span></span>                                |
| <span data-ttu-id="70d35-143">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="70d35-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="70d35-144">false</span><span class="sxs-lookup"><span data-stu-id="70d35-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="70d35-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="70d35-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="70d35-146">Określa nazwę witryny sieci Web serwer sieci Web (IIS), na których chcesz zainstalować tę aplikację sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="70d35-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="70d35-147">Aliasy</span><span class="sxs-lookup"><span data-stu-id="70d35-147">Aliases</span></span>                              | <span data-ttu-id="70d35-148">brak</span><span class="sxs-lookup"><span data-stu-id="70d35-148">none</span></span>                                 |
| <span data-ttu-id="70d35-149">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="70d35-149">Required?</span></span>                            | <span data-ttu-id="70d35-150">false</span><span class="sxs-lookup"><span data-stu-id="70d35-150">false</span></span>                                |
| <span data-ttu-id="70d35-151">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="70d35-151">Position?</span></span>                            | <span data-ttu-id="70d35-152">o nazwie</span><span class="sxs-lookup"><span data-stu-id="70d35-152">named</span></span>                                |
| <span data-ttu-id="70d35-153">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="70d35-153">Default Value</span></span>                        | <span data-ttu-id="70d35-154">Domyślna witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="70d35-154">Default Web Site</span></span>                     |
| <span data-ttu-id="70d35-155">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="70d35-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="70d35-156">false</span><span class="sxs-lookup"><span data-stu-id="70d35-156">false</span></span>                                |
| <span data-ttu-id="70d35-157">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="70d35-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="70d35-158">false</span><span class="sxs-lookup"><span data-stu-id="70d35-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="70d35-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="70d35-159">-Confirm</span></span>

<span data-ttu-id="70d35-160">Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70d35-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="70d35-161">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="70d35-161">Required?</span></span>                            | <span data-ttu-id="70d35-162">false</span><span class="sxs-lookup"><span data-stu-id="70d35-162">false</span></span>                                |
| <span data-ttu-id="70d35-163">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="70d35-163">Position?</span></span>                            | <span data-ttu-id="70d35-164">o nazwie</span><span class="sxs-lookup"><span data-stu-id="70d35-164">named</span></span>                                |
| <span data-ttu-id="70d35-165">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="70d35-165">Default Value</span></span>                        | <span data-ttu-id="70d35-166">false</span><span class="sxs-lookup"><span data-stu-id="70d35-166">false</span></span>                                |
| <span data-ttu-id="70d35-167">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="70d35-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="70d35-168">false</span><span class="sxs-lookup"><span data-stu-id="70d35-168">false</span></span>                                |
| <span data-ttu-id="70d35-169">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="70d35-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="70d35-170">false</span><span class="sxs-lookup"><span data-stu-id="70d35-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="70d35-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="70d35-171">-WhatIf</span></span>

<span data-ttu-id="70d35-172">Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70d35-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="70d35-173">Polecenie cmdlet nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="70d35-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="70d35-174">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="70d35-174">Required?</span></span>                            | <span data-ttu-id="70d35-175">false</span><span class="sxs-lookup"><span data-stu-id="70d35-175">false</span></span>                                |
| <span data-ttu-id="70d35-176">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="70d35-176">Position?</span></span>                            | <span data-ttu-id="70d35-177">o nazwie</span><span class="sxs-lookup"><span data-stu-id="70d35-177">named</span></span>                                |
| <span data-ttu-id="70d35-178">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="70d35-178">Default Value</span></span>                        | <span data-ttu-id="70d35-179">false</span><span class="sxs-lookup"><span data-stu-id="70d35-179">false</span></span>                                |
| <span data-ttu-id="70d35-180">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="70d35-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="70d35-181">false</span><span class="sxs-lookup"><span data-stu-id="70d35-181">false</span></span>                                |
| <span data-ttu-id="70d35-182">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="70d35-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="70d35-183">false</span><span class="sxs-lookup"><span data-stu-id="70d35-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="70d35-184">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="70d35-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="70d35-185">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="70d35-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="70d35-186">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="70d35-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="70d35-187">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="70d35-187">INPUTS</span></span>

<span data-ttu-id="70d35-188">To polecenie cmdlet nie wymaga danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="70d35-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="70d35-189">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="70d35-189">OUTPUTS</span></span>

<span data-ttu-id="70d35-190">To polecenie cmdlet nie generuje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="70d35-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="70d35-191">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="70d35-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="70d35-192">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="70d35-192">EXAMPLE 1</span></span>

<span data-ttu-id="70d35-193">Instalacja przy użyciu wartości domyślnych dla aplikacji sieci web PSWA **WebApplicationName** (*pswa*) i **podaną** (*domyślnej witryny sieci Web* ) parametrów.</span><span class="sxs-lookup"><span data-stu-id="70d35-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="70d35-194">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="70d35-194">EXAMPLE 2</span></span>

<span data-ttu-id="70d35-195">Instalacja aplikacji sieci web PSWA z certyfikatu testowego i przy użyciu wartości domyślnych **WebApplicationName** i **podaną** parametrów.</span><span class="sxs-lookup"><span data-stu-id="70d35-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="70d35-196">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="70d35-196">Related topics</span></span>

- [<span data-ttu-id="70d35-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="70d35-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="70d35-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="70d35-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="70d35-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="70d35-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="70d35-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="70d35-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)