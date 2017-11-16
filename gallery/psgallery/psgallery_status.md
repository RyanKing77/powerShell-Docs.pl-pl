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
<a name="powershell-gallery-status"></a>Stan galerii programu PowerShell
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10/10/2017 — niedostępna przez 2 godziny galerii programu PowerShell 10/10/17

__Podsumowanie wpływ__: galerii programu PowerShell wystąpił okres bardzo duże opóźnienia, co powoduje problemy sporadyczne połączenia, począwszy od około 17: 00 (PDT) 10/10/17. Podczas rozwiązywania problemu, lokacji został przełączony do trybu offline przez 2 godziny uruchamianie około 22: 00 (PDT). Lokacji została przywrócona na krótko przed północy 10/10/2017 r. 
 
__Przyczyna__: głównej przyczyny duże opóźnienie jest nadal badana.

__Rozdzielczość__: usługi sieci web ma się przełączone do trybu offline i przywrócić w celu rozwiązania problemu podstawowego. 

__Następne kroki__: bada głównej przyczyny problemu oryginalnego.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>06/01/2017 - wdrożyć Automatyzacja Azure jest obecnie niedostępna

__Podsumowanie wpływ__: Wdrażanie elementów z zależnościami z galerii programu PowerShell usługi Automatyzacja Azure jest obecnie niedostępny.  Importowanie elementów z galerii programu PowerShell z wewnątrz usługi Automatyzacja Azure jest nadal dostępny.  
 
__Główną przyczynę__: elementy są zależne od siebie, które zostały wcześniej wdrożone usługi Automatyzacja Azure, nie zostanie wdrożone do automatyzacji Azure. Inżynierowie zidentyfikowano problem jak szablony ARM są generowane dla elementów z zależnościami do wdrożenia do funkcji usługi Automatyzacja Azure.

__Rozdzielczość__: współpracy Aby rozwiązać problem.  Bieżące rozwiązanie dla użytkowników jest importowanego elementu galerii programu PowerShell z wewnątrz usługi Automatyzacja Azure. 

__Następne kroki__: inżynierów opublikuje poprawkę wkrótce.  W międzyczasie Użyj zalecane rozwiązania. 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>04/11/2017 — użytkownicy nie może zalogować się przy użyciu konta usługi Azure Active Directory (AAD)

__Podsumowanie wpływ__: Niektórzy użytkownicy nie mogą logować się do galerii programu PowerShell przy użyciu konta usługi Azure AD. 
 
__Główną przyczynę__: podczas aktualizacji do bardziej bezpieczny sposób interakcji z usługi AAD, zmiana ustawienia została pominięta. Testowanie gotowe, aby zweryfikować zmiany nie zawiera niektóre rodzaje konta usługi AAD, więc przystąpiła wdrożenia.

__Rozdzielczość__: inżynierów zidentyfikowane brak ustawienia i naprawić problem. 

__Następne kroki__: Firma Microsoft będzie modyfikowanie testów do uwzględnienia szerszy zestaw typy kont usługi AAD.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017/03/27 — ROZWIĄZANE: nie można wyświetlić poszczególnych stron modułu i skryptu

__Podsumowanie wpływ__: bezpośrednie łącza do pojedynczych stron modułu i skrypt na https://www.powershellgallery.com zostały przerwane. Zgłoszono trwa to we wszystkich regionach. To nie mieć wpływ na dowolnych poleceniach cmdlet PowerShellGet ie., Install-Module skryptu aktualizacji, moduł publikowania, skrypt instalacji, moduł aktualizacji, Opublikuj-Scirpt nadal działają.

__Przyczyna__: inżynierów zaliczyć do przyczynę problemu otworzeniem mediów społecznościowych przycisków, takich jak Facebook na stronę.  

__Rozdzielczość__: inżynierów problem został rozwiązany przez wyłączenie informacje o liczbie usługi Facebook.

__Następne kroki__: możemy otworzyć problemu wewnętrznego śledzenia ustalenie naszych użycia interfejsu API usługi Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>12/15/2016 - nie można wysłać wiadomości e-mail za pośrednictwem PowerShellGallery witryny sieci Web

__Podsumowanie wpływ__: między 2016-12-13 i 2016-12-15, komunikaty wysyłane za pośrednictwem właścicieli kontaktu, zarządzania właścicielami, skontaktuj się z pomocą techniczną lub zgłaszania nadużyć nie zostały odebrane przez administratorów galerii programu PowerShell.  
__Przyczyna__: inżynierów zidentyfikować przyczynę jako problem dotyczący uwierzytelniania z serwerem SMTP.  
__Rozdzielczość__: inżynierów udało się rozwiązać problem dotyczący uwierzytelniania i Przywróć połączenie z serwerem SMTP.  
__Następne kroki__: Jeśli właścicieli kontaktu, zarządzania właścicielami, skontaktuj się z pomocą techniczną lub zgłaszania nadużyć łącza jest używany do wysyłania wiadomości e-mail do cgadmin@microsoft.com podczas tego czasu i firma Microsoft nie udzielono odpowiedzi, spróbuj ponownie. Przepraszamy za ewentualne utrudnienia.  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>Rozwiązane 2016/8-10 -: nie można wysłać wiadomości e-mailcgadmin@microsoft.com

__Podsumowanie wpływ__: między 2016-8-5 oraz 2016-8-10, nie można wysłać wiadomości e-mail zostały klientów cgadmin@microsoft.com, lub użyj funkcji kontakt z nami.  
__Przyczyna__: inżynierów zidentyfikować przyczynę jako zmiana konfiguracji konta e-mail.  
__Rozdzielczość__: inżynierów pracy, aby rozwiązać problem z konfiguracją.  
__Następne kroki__: możesz użyć łącza Skontaktuj się z nami lub wysyłane wiadomości, aby cgadmin@microsoft.com podczas tego czasu i firma Microsoft nie udzielono odpowiedzi, spróbuj ponownie. Dziękujemy za cierpliwość.



## <a name="7132016---download-items-failed"></a>7 13/2016 - pobieranie elementów nie powiodło się

__Podsumowanie wpływ__: między 2016-7-11 i 2016-7-13 podzbiór klientów napotkał problemy pobierania elementów z galerii programu PowerShell. Prawdopodobnie problem sam dyskowe widoczne w następujący komunikat o błędzie zwrócony z instalacji modułu/Install-skryptów i Zapisz skryptu, Zapisz modułu w lub:

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

__Wstępne przyczynę__: inżynierów zidentyfikować problem z Azure zawartości dostarczania Network (CDN), która została wdrożona w galerii programu PowerShell na 2016-7-11.  
__Środki zaradcze__: inżynierów wyłączone Azure CDN w galerii programu PowerShell.  
__Następne kroki__: Znajdź podstawowej główną przyczynę i opracowując rozwiązania, aby uniknąć przyszłych wystąpień.


## <a name="5192016---download-items-failed"></a>5 19/2016 - pobieranie elementów nie powiodło się
__Podsumowanie wpływ__: między 2016-5-17 i 2016-5-19 podzbiór klientów napotkał problemy pobierania elementów z galerii programu PowerShell. Prawdopodobnie problem sam dyskowe widoczne w następujący komunikat o błędzie zwrócony z instalacji modułu/Install-skryptów i Zapisz skryptu, Zapisz modułu w lub:

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

__Wstępne przyczynę__: inżynierów zidentyfikowane awarii w podstawowym dostawcy programu Azure zawartości dostarczania Network (CDN), która została wdrożona w galerii programu PowerShell na 2016-5-17.  
__Środki zaradcze__: inżynierów wyłączone Azure CDN w galerii programu PowerShell.  
__Następne kroki__: Znajdź podstawowej główną przyczynę i opracowując rozwiązania, aby uniknąć przyszłych wystąpień.

