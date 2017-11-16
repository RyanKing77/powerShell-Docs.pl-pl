---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: polecenia cmdlet programu PowerShell
ms.date: 2016-12-12
title: Zainstaluj pswawebapplication
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="9097d-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9097d-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="9097d-104">STRESZCZENIE</span><span class="sxs-lookup"><span data-stu-id="9097d-104">SYNOPSIS</span></span>

<span data-ttu-id="9097d-105">Konfiguruje aplikację sieci web programu Windows PowerShell® Web Access w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="9097d-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="9097d-106">SKŁADNIA</span><span class="sxs-lookup"><span data-stu-id="9097d-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="9097d-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9097d-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="9097d-108">OPIS</span><span class="sxs-lookup"><span data-stu-id="9097d-108">DESCRIPTION</span></span>

<span data-ttu-id="9097d-109">**Install-PswaWebApplication** polecenia cmdlet konfiguruje aplikację sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9097d-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="9097d-110">To polecenie cmdlet instaluje aplikację sieci web, kojarzy go z witryny sieci web i opcjonalnie tworzy, używając certyfikatu SSL testu **useTestCertificate** parametru.</span><span class="sxs-lookup"><span data-stu-id="9097d-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="9097d-111">Dla bezpieczeństwa przyczyny Administratorzy sieci web nie należy używać certyfikatu testowego dla środowisk produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="9097d-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="9097d-112">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="9097d-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="9097d-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="9097d-113">-UseTestCertificate</span></span>

<span data-ttu-id="9097d-114">Określa, czy certyfikat testowy został utworzony.</span><span class="sxs-lookup"><span data-stu-id="9097d-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="9097d-115">Jeśli ten parametr ma ustawioną wartość PRAWDA, to polecenie cmdlet tworzy certyfikat testowy i konfiguruje aplikację sieci web programu Windows PowerShell Web Access do używania certyfikatu dla żądania HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9097d-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="9097d-116">Jeśli ten parametr ma wartość false, następnie nie certyfikatu powiązania jest utworzone lub.</span><span class="sxs-lookup"><span data-stu-id="9097d-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="9097d-117">Wartość tę należy ustawić na wartość false, jeśli inny certyfikat jest używany dla programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9097d-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="9097d-118">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9097d-118">Aliases</span></span>                              | <span data-ttu-id="9097d-119">brak</span><span class="sxs-lookup"><span data-stu-id="9097d-119">none</span></span>                                 |
| <span data-ttu-id="9097d-120">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9097d-120">Required?</span></span>                            | <span data-ttu-id="9097d-121">false</span><span class="sxs-lookup"><span data-stu-id="9097d-121">false</span></span>                                |
| <span data-ttu-id="9097d-122">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9097d-122">Position?</span></span>                            | <span data-ttu-id="9097d-123">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9097d-123">named</span></span>                                |
| <span data-ttu-id="9097d-124">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9097d-124">Default Value</span></span>                        | <span data-ttu-id="9097d-125">Wartość true</span><span class="sxs-lookup"><span data-stu-id="9097d-125">true</span></span>                                 |
| <span data-ttu-id="9097d-126">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9097d-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9097d-127">false</span><span class="sxs-lookup"><span data-stu-id="9097d-127">false</span></span>                                |
| <span data-ttu-id="9097d-128">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9097d-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9097d-129">false</span><span class="sxs-lookup"><span data-stu-id="9097d-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="9097d-130">-WebApplicationName&lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="9097d-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="9097d-131">Określa nazwę aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="9097d-131">Specifies the name for your web application.</span></span> <span data-ttu-id="9097d-132">Jest on wyświetlany jako ostatnia część adres URL programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9097d-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="9097d-133">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9097d-133">Aliases</span></span>                              | <span data-ttu-id="9097d-134">brak</span><span class="sxs-lookup"><span data-stu-id="9097d-134">none</span></span>                                 |
| <span data-ttu-id="9097d-135">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9097d-135">Required?</span></span>                            | <span data-ttu-id="9097d-136">false</span><span class="sxs-lookup"><span data-stu-id="9097d-136">false</span></span>                                |
| <span data-ttu-id="9097d-137">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9097d-137">Position?</span></span>                            | <span data-ttu-id="9097d-138">1</span><span class="sxs-lookup"><span data-stu-id="9097d-138">1</span></span>                                    |
| <span data-ttu-id="9097d-139">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9097d-139">Default Value</span></span>                        | <span data-ttu-id="9097d-140">pswa</span><span class="sxs-lookup"><span data-stu-id="9097d-140">pswa</span></span>                                 |
| <span data-ttu-id="9097d-141">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9097d-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9097d-142">false</span><span class="sxs-lookup"><span data-stu-id="9097d-142">false</span></span>                                |
| <span data-ttu-id="9097d-143">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9097d-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9097d-144">false</span><span class="sxs-lookup"><span data-stu-id="9097d-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="9097d-145">-Podaną&lt;ciągu&gt;</span><span class="sxs-lookup"><span data-stu-id="9097d-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="9097d-146">Określa nazwę witryny sieci Web serwer sieci Web (IIS), na których chcesz zainstalować tę aplikację sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9097d-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="9097d-147">Aliasy</span><span class="sxs-lookup"><span data-stu-id="9097d-147">Aliases</span></span>                              | <span data-ttu-id="9097d-148">brak</span><span class="sxs-lookup"><span data-stu-id="9097d-148">none</span></span>                                 |
| <span data-ttu-id="9097d-149">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9097d-149">Required?</span></span>                            | <span data-ttu-id="9097d-150">false</span><span class="sxs-lookup"><span data-stu-id="9097d-150">false</span></span>                                |
| <span data-ttu-id="9097d-151">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9097d-151">Position?</span></span>                            | <span data-ttu-id="9097d-152">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9097d-152">named</span></span>                                |
| <span data-ttu-id="9097d-153">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9097d-153">Default Value</span></span>                        | <span data-ttu-id="9097d-154">Domyślna witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="9097d-154">Default Web Site</span></span>                     |
| <span data-ttu-id="9097d-155">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9097d-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9097d-156">false</span><span class="sxs-lookup"><span data-stu-id="9097d-156">false</span></span>                                |
| <span data-ttu-id="9097d-157">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9097d-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9097d-158">false</span><span class="sxs-lookup"><span data-stu-id="9097d-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="9097d-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9097d-159">-Confirm</span></span>

<span data-ttu-id="9097d-160">Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9097d-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="9097d-161">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9097d-161">Required?</span></span>                            | <span data-ttu-id="9097d-162">false</span><span class="sxs-lookup"><span data-stu-id="9097d-162">false</span></span>                                |
| <span data-ttu-id="9097d-163">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9097d-163">Position?</span></span>                            | <span data-ttu-id="9097d-164">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9097d-164">named</span></span>                                |
| <span data-ttu-id="9097d-165">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9097d-165">Default Value</span></span>                        | <span data-ttu-id="9097d-166">false</span><span class="sxs-lookup"><span data-stu-id="9097d-166">false</span></span>                                |
| <span data-ttu-id="9097d-167">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9097d-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9097d-168">false</span><span class="sxs-lookup"><span data-stu-id="9097d-168">false</span></span>                                |
| <span data-ttu-id="9097d-169">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9097d-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9097d-170">false</span><span class="sxs-lookup"><span data-stu-id="9097d-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="9097d-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9097d-171">-WhatIf</span></span>

<span data-ttu-id="9097d-172">Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9097d-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9097d-173">Polecenie cmdlet nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="9097d-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="9097d-174">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="9097d-174">Required?</span></span>                            | <span data-ttu-id="9097d-175">false</span><span class="sxs-lookup"><span data-stu-id="9097d-175">false</span></span>                                |
| <span data-ttu-id="9097d-176">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="9097d-176">Position?</span></span>                            | <span data-ttu-id="9097d-177">o nazwie</span><span class="sxs-lookup"><span data-stu-id="9097d-177">named</span></span>                                |
| <span data-ttu-id="9097d-178">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9097d-178">Default Value</span></span>                        | <span data-ttu-id="9097d-179">false</span><span class="sxs-lookup"><span data-stu-id="9097d-179">false</span></span>                                |
| <span data-ttu-id="9097d-180">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="9097d-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9097d-181">false</span><span class="sxs-lookup"><span data-stu-id="9097d-181">false</span></span>                                |
| <span data-ttu-id="9097d-182">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="9097d-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9097d-183">false</span><span class="sxs-lookup"><span data-stu-id="9097d-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="9097d-184">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="9097d-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="9097d-185">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer i - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="9097d-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="9097d-186">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9097d-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="9097d-187">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="9097d-187">INPUTS</span></span>

<span data-ttu-id="9097d-188">To polecenie cmdlet nie wymaga danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="9097d-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="9097d-189">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="9097d-189">OUTPUTS</span></span>

<span data-ttu-id="9097d-190">To polecenie cmdlet nie generuje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9097d-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="9097d-191">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="9097d-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="9097d-192">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="9097d-192">EXAMPLE 1</span></span>

<span data-ttu-id="9097d-193">Instalacja przy użyciu wartości domyślnych dla aplikacji sieci web PSWA **WebApplicationName** (*pswa*) i **podaną** (*domyślnej witryny sieci Web* ) parametrów.</span><span class="sxs-lookup"><span data-stu-id="9097d-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="9097d-194">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="9097d-194">EXAMPLE 2</span></span>

<span data-ttu-id="9097d-195">Instalacja aplikacji sieci web PSWA z certyfikatu testowego i przy użyciu wartości domyślnych **WebApplicationName** i **podaną** parametrów.</span><span class="sxs-lookup"><span data-stu-id="9097d-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="9097d-196">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="9097d-196">Related topics</span></span>

- [<span data-ttu-id="9097d-197">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9097d-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="9097d-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9097d-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="9097d-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9097d-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="9097d-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9097d-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
