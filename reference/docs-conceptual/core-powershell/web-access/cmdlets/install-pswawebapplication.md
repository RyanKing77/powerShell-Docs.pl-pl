---
ms.topic: reference
keywords: polecenia cmdlet programu PowerShell
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268303"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="2b21b-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2b21b-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="2b21b-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2b21b-104">SYNOPSIS</span></span>

<span data-ttu-id="2b21b-105">Umożliwia skonfigurowanie aplikacji sieci web programu Windows PowerShell Web Access w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="2b21b-105">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b21b-106">SKŁADNIA</span><span class="sxs-lookup"><span data-stu-id="2b21b-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="2b21b-107">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="2b21b-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2b21b-108">OPIS</span><span class="sxs-lookup"><span data-stu-id="2b21b-108">DESCRIPTION</span></span>

<span data-ttu-id="2b21b-109">**Install-PswaWebApplication** polecenie cmdlet umożliwia skonfigurowanie aplikacji sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="2b21b-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span>
<span data-ttu-id="2b21b-110">To polecenie cmdlet instaluje aplikację sieci web, kojarzy ją z witryny sieci web i opcjonalnie tworzy test SSL certyfikatu przy użyciu **useTestCertificate** parametru.</span><span class="sxs-lookup"><span data-stu-id="2b21b-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="2b21b-111">Dla bezpieczeństwa przyczyny Administratorzy sieci web nie należy używać certyfikatu testowego w środowiskach produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="2b21b-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="2b21b-112">PARAMETRY</span><span class="sxs-lookup"><span data-stu-id="2b21b-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="2b21b-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="2b21b-113">-UseTestCertificate</span></span>

<span data-ttu-id="2b21b-114">Określa, czy certyfikat testowy został utworzony.</span><span class="sxs-lookup"><span data-stu-id="2b21b-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="2b21b-115">Jeśli ten parametr ma wartość true, to polecenie cmdlet tworzy certyfikat testowy i konfiguruje aplikację sieci web programu Windows PowerShell Web Access, aby użyć certyfikatu dla żądania HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2b21b-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="2b21b-116">Jeśli ten parametr ma wartość false, następnie nie powiązania lub certyfikat zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="2b21b-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="2b21b-117">Wartość tę należy ustawić na wartość false, jeśli jest używany inny certyfikat, programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="2b21b-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="2b21b-118">Aliasy</span><span class="sxs-lookup"><span data-stu-id="2b21b-118">Aliases</span></span>                              | <span data-ttu-id="2b21b-119">brak</span><span class="sxs-lookup"><span data-stu-id="2b21b-119">none</span></span>                                 |
| <span data-ttu-id="2b21b-120">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="2b21b-120">Required?</span></span>                            | <span data-ttu-id="2b21b-121">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-121">false</span></span>                                |
| <span data-ttu-id="2b21b-122">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="2b21b-122">Position?</span></span>                            | <span data-ttu-id="2b21b-123">o nazwie</span><span class="sxs-lookup"><span data-stu-id="2b21b-123">named</span></span>                                |
| <span data-ttu-id="2b21b-124">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="2b21b-124">Default Value</span></span>                        | <span data-ttu-id="2b21b-125">true</span><span class="sxs-lookup"><span data-stu-id="2b21b-125">true</span></span>                                 |
| <span data-ttu-id="2b21b-126">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="2b21b-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b21b-127">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-127">false</span></span>                                |
| <span data-ttu-id="2b21b-128">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="2b21b-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b21b-129">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-129">false</span></span>                                |

### <a name="-webapplicationname"></a><span data-ttu-id="2b21b-130">-WebApplicationName</span><span class="sxs-lookup"><span data-stu-id="2b21b-130">-WebApplicationName</span></span>

<span data-ttu-id="2b21b-131">Określa nazwę aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="2b21b-131">Specifies the name for your web application.</span></span> <span data-ttu-id="2b21b-132">Jest on wyświetlany jako ostatnia część adres URL programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="2b21b-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="2b21b-133">Aliasy</span><span class="sxs-lookup"><span data-stu-id="2b21b-133">Aliases</span></span>                              | <span data-ttu-id="2b21b-134">brak</span><span class="sxs-lookup"><span data-stu-id="2b21b-134">none</span></span>                                 |
| <span data-ttu-id="2b21b-135">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="2b21b-135">Required?</span></span>                            | <span data-ttu-id="2b21b-136">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-136">false</span></span>                                |
| <span data-ttu-id="2b21b-137">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="2b21b-137">Position?</span></span>                            | <span data-ttu-id="2b21b-138">1</span><span class="sxs-lookup"><span data-stu-id="2b21b-138">1</span></span>                                    |
| <span data-ttu-id="2b21b-139">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="2b21b-139">Default Value</span></span>                        | <span data-ttu-id="2b21b-140">pswa</span><span class="sxs-lookup"><span data-stu-id="2b21b-140">pswa</span></span>                                 |
| <span data-ttu-id="2b21b-141">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="2b21b-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b21b-142">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-142">false</span></span>                                |
| <span data-ttu-id="2b21b-143">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="2b21b-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b21b-144">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-144">false</span></span>                                |

### <a name="-websitename"></a><span data-ttu-id="2b21b-145">-Podaną nazwą</span><span class="sxs-lookup"><span data-stu-id="2b21b-145">-WebSiteName</span></span>

<span data-ttu-id="2b21b-146">Określa nazwę witryny sieci Web serwer sieci Web (IIS), na którym chcesz zainstalować tę aplikację sieci web programu Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="2b21b-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="2b21b-147">Aliasy</span><span class="sxs-lookup"><span data-stu-id="2b21b-147">Aliases</span></span>                              | <span data-ttu-id="2b21b-148">brak</span><span class="sxs-lookup"><span data-stu-id="2b21b-148">none</span></span>                                 |
| <span data-ttu-id="2b21b-149">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="2b21b-149">Required?</span></span>                            | <span data-ttu-id="2b21b-150">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-150">false</span></span>                                |
| <span data-ttu-id="2b21b-151">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="2b21b-151">Position?</span></span>                            | <span data-ttu-id="2b21b-152">o nazwie</span><span class="sxs-lookup"><span data-stu-id="2b21b-152">named</span></span>                                |
| <span data-ttu-id="2b21b-153">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="2b21b-153">Default Value</span></span>                        | <span data-ttu-id="2b21b-154">Domyślna witryna sieci Web</span><span class="sxs-lookup"><span data-stu-id="2b21b-154">Default Web Site</span></span>                     |
| <span data-ttu-id="2b21b-155">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="2b21b-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b21b-156">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-156">false</span></span>                                |
| <span data-ttu-id="2b21b-157">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="2b21b-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b21b-158">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="2b21b-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2b21b-159">-Confirm</span></span>

<span data-ttu-id="2b21b-160">Monituje o potwierdzenie przed uruchomieniem polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b21b-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="2b21b-161">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="2b21b-161">Required?</span></span>                            | <span data-ttu-id="2b21b-162">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-162">false</span></span>                                |
| <span data-ttu-id="2b21b-163">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="2b21b-163">Position?</span></span>                            | <span data-ttu-id="2b21b-164">o nazwie</span><span class="sxs-lookup"><span data-stu-id="2b21b-164">named</span></span>                                |
| <span data-ttu-id="2b21b-165">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="2b21b-165">Default Value</span></span>                        | <span data-ttu-id="2b21b-166">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-166">false</span></span>                                |
| <span data-ttu-id="2b21b-167">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="2b21b-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b21b-168">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-168">false</span></span>                                |
| <span data-ttu-id="2b21b-169">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="2b21b-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b21b-170">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="2b21b-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2b21b-171">-WhatIf</span></span>

<span data-ttu-id="2b21b-172">Pokazuje, co się stanie po uruchomieniu polecenia cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b21b-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2b21b-173">Polecenie cmdlet nie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="2b21b-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="2b21b-174">Wymagane?</span><span class="sxs-lookup"><span data-stu-id="2b21b-174">Required?</span></span>                            | <span data-ttu-id="2b21b-175">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-175">false</span></span>                                |
| <span data-ttu-id="2b21b-176">Pozycja?</span><span class="sxs-lookup"><span data-stu-id="2b21b-176">Position?</span></span>                            | <span data-ttu-id="2b21b-177">o nazwie</span><span class="sxs-lookup"><span data-stu-id="2b21b-177">named</span></span>                                |
| <span data-ttu-id="2b21b-178">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="2b21b-178">Default Value</span></span>                        | <span data-ttu-id="2b21b-179">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-179">false</span></span>                                |
| <span data-ttu-id="2b21b-180">Akceptowanie danych wejściowych potoku?</span><span class="sxs-lookup"><span data-stu-id="2b21b-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2b21b-181">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-181">false</span></span>                                |
| <span data-ttu-id="2b21b-182">Akceptowanie symboli wieloznacznych?</span><span class="sxs-lookup"><span data-stu-id="2b21b-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2b21b-183">false</span><span class="sxs-lookup"><span data-stu-id="2b21b-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2b21b-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2b21b-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2b21b-185">To polecenie cmdlet obsługuje typowe parametry:-Verbose,-Debug, - ErrorAction, - ErrorVariable,-OutBuffer oraz - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="2b21b-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span> <span data-ttu-id="2b21b-186">Aby uzyskać więcej informacji, zobacz [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2b21b-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="2b21b-187">DANE WEJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="2b21b-187">INPUTS</span></span>

<span data-ttu-id="2b21b-188">To polecenie cmdlet nie wymaga danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="2b21b-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="2b21b-189">DANE WYJŚCIOWE</span><span class="sxs-lookup"><span data-stu-id="2b21b-189">OUTPUTS</span></span>

<span data-ttu-id="2b21b-190">To polecenie cmdlet nie generuje żadnych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2b21b-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="2b21b-191">PRZYKŁADY</span><span class="sxs-lookup"><span data-stu-id="2b21b-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2b21b-192">PRZYKŁAD 1</span><span class="sxs-lookup"><span data-stu-id="2b21b-192">EXAMPLE 1</span></span>

<span data-ttu-id="2b21b-193">W tym przykładzie instaluje przy użyciu wartości domyślnych dla aplikacji sieci web PSWA **WebApplicationName** (*pswa*) i **podaną nazwą** (*domyślna witryna sieci Web* ) parametry.</span><span class="sxs-lookup"><span data-stu-id="2b21b-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="2b21b-194">PRZYKŁAD 2</span><span class="sxs-lookup"><span data-stu-id="2b21b-194">EXAMPLE 2</span></span>

<span data-ttu-id="2b21b-195">W tym przykładzie instaluje PSWA aplikacji sieci web przy użyciu certyfikatu testowego i przy użyciu wartości domyślnych dla **WebApplicationName** i **podaną nazwą** parametrów.</span><span class="sxs-lookup"><span data-stu-id="2b21b-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="2b21b-196">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="2b21b-196">Related topics</span></span>

- [<span data-ttu-id="2b21b-197">Polecenia Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b21b-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="2b21b-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b21b-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="2b21b-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b21b-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="2b21b-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2b21b-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)