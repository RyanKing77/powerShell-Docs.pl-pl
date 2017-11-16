---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="19808-103">Stan galerii programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="19808-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="19808-104">10/10/2017 — niedostępna przez 2 godziny galerii programu PowerShell 10/10/17</span><span class="sxs-lookup"><span data-stu-id="19808-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="19808-105">__Podsumowanie wpływ__: galerii programu PowerShell wystąpił okres bardzo duże opóźnienia, co powoduje problemy sporadyczne połączenia, począwszy od około 17: 00 (PDT) 10/10/17.</span><span class="sxs-lookup"><span data-stu-id="19808-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="19808-106">Podczas rozwiązywania problemu, lokacji został przełączony do trybu offline przez 2 godziny uruchamianie około 22: 00 (PDT).</span><span class="sxs-lookup"><span data-stu-id="19808-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="19808-107">Lokacji została przywrócona na krótko przed północy 10/10/2017 r.</span><span class="sxs-lookup"><span data-stu-id="19808-107">The site was restored shortly before midnight 10/10/2017.</span></span> 
 
<span data-ttu-id="19808-108">__Przyczyna__: głównej przyczyny duże opóźnienie jest nadal badana.</span><span class="sxs-lookup"><span data-stu-id="19808-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="19808-109">__Rozdzielczość__: usługi sieci web ma się przełączone do trybu offline i przywrócić w celu rozwiązania problemu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="19808-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span> 

<span data-ttu-id="19808-110">__Następne kroki__: bada głównej przyczyny problemu oryginalnego.</span><span class="sxs-lookup"><span data-stu-id="19808-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="19808-111">06/01/2017 - wdrożyć Automatyzacja Azure jest obecnie niedostępna</span><span class="sxs-lookup"><span data-stu-id="19808-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="19808-112">__Podsumowanie wpływ__: Wdrażanie elementów z zależnościami z galerii programu PowerShell usługi Automatyzacja Azure jest obecnie niedostępny.</span><span class="sxs-lookup"><span data-stu-id="19808-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="19808-113">Importowanie elementów z galerii programu PowerShell z wewnątrz usługi Automatyzacja Azure jest nadal dostępny.</span><span class="sxs-lookup"><span data-stu-id="19808-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="19808-114">__Główną przyczynę__: elementy są zależne od siebie, które zostały wcześniej wdrożone usługi Automatyzacja Azure, nie zostanie wdrożone do automatyzacji Azure.</span><span class="sxs-lookup"><span data-stu-id="19808-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="19808-115">Inżynierowie zidentyfikowano problem jak szablony ARM są generowane dla elementów z zależnościami do wdrożenia do funkcji usługi Automatyzacja Azure.</span><span class="sxs-lookup"><span data-stu-id="19808-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="19808-116">__Rozdzielczość__: współpracy Aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="19808-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="19808-117">Bieżące rozwiązanie dla użytkowników jest importowanego elementu galerii programu PowerShell z wewnątrz usługi Automatyzacja Azure.</span><span class="sxs-lookup"><span data-stu-id="19808-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="19808-118">__Następne kroki__: inżynierów opublikuje poprawkę wkrótce.</span><span class="sxs-lookup"><span data-stu-id="19808-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="19808-119">W międzyczasie Użyj zalecane rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="19808-119">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="19808-120">04/11/2017 — użytkownicy nie może zalogować się przy użyciu konta usługi Azure Active Directory (AAD)</span><span class="sxs-lookup"><span data-stu-id="19808-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="19808-121">__Podsumowanie wpływ__: Niektórzy użytkownicy nie mogą logować się do galerii programu PowerShell przy użyciu konta usługi Azure AD.</span><span class="sxs-lookup"><span data-stu-id="19808-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="19808-122">__Główną przyczynę__: podczas aktualizacji do bardziej bezpieczny sposób interakcji z usługi AAD, zmiana ustawienia została pominięta.</span><span class="sxs-lookup"><span data-stu-id="19808-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="19808-123">Testowanie gotowe, aby zweryfikować zmiany nie zawiera niektóre rodzaje konta usługi AAD, więc przystąpiła wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="19808-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="19808-124">__Rozdzielczość__: inżynierów zidentyfikowane brak ustawienia i naprawić problem.</span><span class="sxs-lookup"><span data-stu-id="19808-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="19808-125">__Następne kroki__: Firma Microsoft będzie modyfikowanie testów do uwzględnienia szerszy zestaw typy kont usługi AAD.</span><span class="sxs-lookup"><span data-stu-id="19808-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="19808-126">2017/03/27 — ROZWIĄZANE: nie można wyświetlić poszczególnych stron modułu i skryptu</span><span class="sxs-lookup"><span data-stu-id="19808-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="19808-127">__Podsumowanie wpływ__: bezpośrednie łącza do pojedynczych stron modułu i skrypt na https://www.powershellgallery.com zostały przerwane.</span><span class="sxs-lookup"><span data-stu-id="19808-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="19808-128">Zgłoszono trwa to we wszystkich regionach.</span><span class="sxs-lookup"><span data-stu-id="19808-128">This was being reported across all the regions.</span></span> <span data-ttu-id="19808-129">To nie mieć wpływ na dowolnych poleceniach cmdlet PowerShellGet ie., Install-Module skryptu aktualizacji, moduł publikowania, skrypt instalacji, moduł aktualizacji, Opublikuj-Scirpt nadal działają.</span><span class="sxs-lookup"><span data-stu-id="19808-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="19808-130">__Przyczyna__: inżynierów zaliczyć do przyczynę problemu otworzeniem mediów społecznościowych przycisków, takich jak Facebook na stronę.</span><span class="sxs-lookup"><span data-stu-id="19808-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="19808-131">__Rozdzielczość__: inżynierów problem został rozwiązany przez wyłączenie informacje o liczbie usługi Facebook.</span><span class="sxs-lookup"><span data-stu-id="19808-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="19808-132">__Następne kroki__: możemy otworzyć problemu wewnętrznego śledzenia ustalenie naszych użycia interfejsu API usługi Facebook.</span><span class="sxs-lookup"><span data-stu-id="19808-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="19808-133">12/15/2016 - nie można wysłać wiadomości e-mail za pośrednictwem PowerShellGallery witryny sieci Web</span><span class="sxs-lookup"><span data-stu-id="19808-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="19808-134">__Podsumowanie wpływ__: między 2016-12-13 i 2016-12-15, komunikaty wysyłane za pośrednictwem właścicieli kontaktu, zarządzania właścicielami, skontaktuj się z pomocą techniczną lub zgłaszania nadużyć nie zostały odebrane przez administratorów galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19808-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="19808-135">__Przyczyna__: inżynierów zidentyfikować przyczynę jako problem dotyczący uwierzytelniania z serwerem SMTP.</span><span class="sxs-lookup"><span data-stu-id="19808-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="19808-136">__Rozdzielczość__: inżynierów udało się rozwiązać problem dotyczący uwierzytelniania i Przywróć połączenie z serwerem SMTP.</span><span class="sxs-lookup"><span data-stu-id="19808-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="19808-137">__Następne kroki__: Jeśli właścicieli kontaktu, zarządzania właścicielami, skontaktuj się z pomocą techniczną lub zgłaszania nadużyć łącza jest używany do wysyłania wiadomości e-mail do cgadmin@microsoft.com podczas tego czasu i firma Microsoft nie udzielono odpowiedzi, spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="19808-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="19808-138">Przepraszamy za ewentualne utrudnienia.</span><span class="sxs-lookup"><span data-stu-id="19808-138">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="19808-139">Rozwiązane 2016/8-10 -: nie można wysłać wiadomości e-mailcgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="19808-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="19808-140">__Podsumowanie wpływ__: między 2016-8-5 oraz 2016-8-10, nie można wysłać wiadomości e-mail zostały klientów cgadmin@microsoft.com, lub użyj funkcji kontakt z nami.</span><span class="sxs-lookup"><span data-stu-id="19808-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="19808-141">__Przyczyna__: inżynierów zidentyfikować przyczynę jako zmiana konfiguracji konta e-mail.</span><span class="sxs-lookup"><span data-stu-id="19808-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="19808-142">__Rozdzielczość__: inżynierów pracy, aby rozwiązać problem z konfiguracją.</span><span class="sxs-lookup"><span data-stu-id="19808-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="19808-143">__Następne kroki__: możesz użyć łącza Skontaktuj się z nami lub wysyłane wiadomości, aby cgadmin@microsoft.com podczas tego czasu i firma Microsoft nie udzielono odpowiedzi, spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="19808-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="19808-144">Dziękujemy za cierpliwość.</span><span class="sxs-lookup"><span data-stu-id="19808-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="19808-145">7 13/2016 - pobieranie elementów nie powiodło się</span><span class="sxs-lookup"><span data-stu-id="19808-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="19808-146">__Podsumowanie wpływ__: między 2016-7-11 i 2016-7-13 podzbiór klientów napotkał problemy pobierania elementów z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19808-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="19808-147">Prawdopodobnie problem sam dyskowe widoczne w następujący komunikat o błędzie zwrócony z instalacji modułu/Install-skryptów i Zapisz skryptu, Zapisz modułu w lub:</span><span class="sxs-lookup"><span data-stu-id="19808-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="19808-148">__Wstępne przyczynę__: inżynierów zidentyfikować problem z Azure zawartości dostarczania Network (CDN), która została wdrożona w galerii programu PowerShell na 2016-7-11.</span><span class="sxs-lookup"><span data-stu-id="19808-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="19808-149">__Środki zaradcze__: inżynierów wyłączone Azure CDN w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19808-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="19808-150">__Następne kroki__: Znajdź podstawowej główną przyczynę i opracowując rozwiązania, aby uniknąć przyszłych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="19808-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="19808-151">5 19/2016 - pobieranie elementów nie powiodło się</span><span class="sxs-lookup"><span data-stu-id="19808-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="19808-152">__Podsumowanie wpływ__: między 2016-5-17 i 2016-5-19 podzbiór klientów napotkał problemy pobierania elementów z galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19808-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="19808-153">Prawdopodobnie problem sam dyskowe widoczne w następujący komunikat o błędzie zwrócony z instalacji modułu/Install-skryptów i Zapisz skryptu, Zapisz modułu w lub:</span><span class="sxs-lookup"><span data-stu-id="19808-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="19808-154">__Wstępne przyczynę__: inżynierów zidentyfikowane awarii w podstawowym dostawcy programu Azure zawartości dostarczania Network (CDN), która została wdrożona w galerii programu PowerShell na 2016-5-17.</span><span class="sxs-lookup"><span data-stu-id="19808-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="19808-155">__Środki zaradcze__: inżynierów wyłączone Azure CDN w galerii programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="19808-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="19808-156">__Następne kroki__: Znajdź podstawowej główną przyczynę i opracowując rozwiązania, aby uniknąć przyszłych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="19808-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

