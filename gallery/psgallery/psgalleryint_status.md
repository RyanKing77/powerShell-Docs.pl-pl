---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgalleryint_status
ms.openlocfilehash: 4f7d300bb07fcbdb100c2fb029f8f66ab260fe7a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a><span data-ttu-id="40e08-103">Stan galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="40e08-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="40e08-104">2017/03/27 — ROZWIĄZANE: nie można wyświetlić poszczególnych stron modułu i skryptu</span><span class="sxs-lookup"><span data-stu-id="40e08-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="40e08-105">__Podsumowanie wpływ__: bezpośrednie łącza do pojedynczych stron modułu i skrypt na https://www.powershellgallery.com zostały przerwane.</span><span class="sxs-lookup"><span data-stu-id="40e08-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="40e08-106">Zgłoszono trwa to we wszystkich regionach.</span><span class="sxs-lookup"><span data-stu-id="40e08-106">This was being reported across all the regions.</span></span> <span data-ttu-id="40e08-107">To nie mieć wpływ na dowolnych poleceniach cmdlet PowerShellGet ie., Install-Module skryptów publikowania skryptu aktualizacji, moduł publikowania, skrypt instalacji, moduł aktualizacji, nadal działają.</span><span class="sxs-lookup"><span data-stu-id="40e08-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="40e08-108">__Przyczyna__: inżynierów zaliczyć do przyczynę problemu otworzeniem mediów społecznościowych przycisków, takich jak Facebook na stronę.</span><span class="sxs-lookup"><span data-stu-id="40e08-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>

<span data-ttu-id="40e08-109">__Rozdzielczość__: inżynierów problem został rozwiązany przez wyłączenie informacje o liczbie usługi Facebook.</span><span class="sxs-lookup"><span data-stu-id="40e08-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="40e08-110">__Następne kroki__: możemy otworzyć problemu wewnętrznego śledzenia ustalenie naszych użycia interfejsu API usługi Facebook.</span><span class="sxs-lookup"><span data-stu-id="40e08-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="40e08-111">12/15/2016 - nie można wysłać wiadomości e-mail za pośrednictwem PowerShellGallery witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="40e08-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="40e08-112">__Podsumowanie wpływ__: między 2016-12-13 i 2016-12-15, komunikaty wysyłane za pośrednictwem właścicieli kontaktu, zarządzania właścicielami, skontaktuj się z pomocą techniczną lub zgłaszania nadużyć nie zostały odebrane przez administratorów galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40e08-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="40e08-113">__Przyczyna__: inżynierów zidentyfikować przyczynę jako problem dotyczący uwierzytelniania z serwerem SMTP.</span><span class="sxs-lookup"><span data-stu-id="40e08-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>
<span data-ttu-id="40e08-114">__Rozdzielczość__: inżynierów udało się rozwiązać problem dotyczący uwierzytelniania i Przywróć połączenie z serwerem SMTP.</span><span class="sxs-lookup"><span data-stu-id="40e08-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>
<span data-ttu-id="40e08-115">__Następne kroki__: Jeśli właścicieli kontaktu, zarządzania właścicielami, skontaktuj się z pomocą techniczną lub zgłaszania nadużyć łącza jest używany do wysyłania wiadomości e-mail do cgadmin@microsoft.com podczas tego czasu i firma Microsoft nie udzielono odpowiedzi, spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="40e08-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="40e08-116">Przepraszamy za ewentualne utrudnienia.</span><span class="sxs-lookup"><span data-stu-id="40e08-116">We apologize for the inconvenience.</span></span>


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="40e08-117">Rozwiązane 2016/8-10 -: nie można wysłać wiadomości e-mail cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="40e08-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="40e08-118">__Podsumowanie wpływ__: między 2016-8-5 oraz 2016-8-10, nie można wysłać wiadomości e-mail zostały klientów cgadmin@microsoft.com, lub użyj funkcji kontakt z nami.</span><span class="sxs-lookup"><span data-stu-id="40e08-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>
<span data-ttu-id="40e08-119">__Przyczyna__: inżynierów zidentyfikować przyczynę jako zmiana konfiguracji konta e-mail.</span><span class="sxs-lookup"><span data-stu-id="40e08-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>
<span data-ttu-id="40e08-120">__Rozdzielczość__: inżynierów pracy, aby rozwiązać problem z konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="40e08-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>
<span data-ttu-id="40e08-121">__Następne kroki__: możesz użyć łącza Skontaktuj się z nami lub wysyłane wiadomości, aby cgadmin@microsoft.com podczas tego czasu i firma Microsoft nie udzielono odpowiedzi, spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="40e08-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="40e08-122">Dziękujemy za cierpliwość.</span><span class="sxs-lookup"><span data-stu-id="40e08-122">Thank you for your patience.</span></span>