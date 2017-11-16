---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: Galeria, programu powershell, polecenia cmdlet, psgallery
title: Tworzenie i publikowanie elementu
ms.openlocfilehash: b6bcd3e923b77ad7d19a1d92aeb78222bff7ea7e
ms.sourcegitcommit: e08f036021e9f115dbb52c697941706cc4ee51dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2017
---
# <a name="creating-and-publishing-an-item"></a>Tworzenie i publikowanie elementu 
Galerii programu PowerShell jest używana do publikowania i udostępniania szerszych społeczności użytkowników programu PowerShell stabilna moduły programu PowerShell, skrypty i zasobów usługi Konfiguracja DSC.    

W tym artykule omówiono mechanika i ważne czynności Przygotowywanie skryptu lub modułu i opublikować galerii programu PowerShell.
Zdecydowanie zaleca się przejrzenie [wskazówki dotyczące publikowania](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) sposób upewnić się, że elementy publikowania zostanie szerzej zaakceptowane przez użytkowników galerii programu PowerShell. 

Minimalne wymagania, aby opublikować element galerii programu PowerShell są:

* Konta galerii programu PowerShell, i skojarzony klucz interfejsu API
* Upewnij się, że jest wymagane metadane w tego elementu
* Upewnij się, że tego elementu jest gotowa do opublikowania za pomocą narzędzi wstępnej weryfikacji
* Publikowanie elementu w galerii programu PowerShell przy użyciu polecenia Publish-Module i opublikuj skryptu
* Odpowiadanie na pytań lub wątpliwości dotyczących tego elementu
 
Galerii programu PowerShell akceptuje moduły programu PowerShell i skryptów programu PowerShell. Gdy firma Microsoft odwołują się do skryptów, możemy oznacza skrypt PowerShell, który jest pojedynczy plik, a nie jest częścią większej modułu. 

## <a name="powershell-gallery-account-and-api-key"></a>Konto galerii programu PowerShell i klucz interfejsu API
Zobacz [tworzenia konta galerii programu PowerShell](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) jak skonfigurować konto galerii programu PowerShell. 

Po utworzeniu konta, możesz uzyskać klucz interfejsu API wymagane do publikowania elementu.
Po zalogowaniu się przy użyciu konta, nazwy użytkownika pojawi się w górnej części strony galerii programu PowerShell zamiast rejestru. Kliknięcie nazwy użytkownika spowoduje przejście do strony Moje konto, gdzie można znaleźć klucz interfejsu API. 

Uwaga: Klucz interfejsu API muszą być traktowane jako nazwy logowania i hasła bezpiecznego. Przy użyciu tego klucza, ani osób, można zaktualizować dowolny element, którego jesteś właścicielem w galerii programu PowerShell. Zalecamy zaktualizowanie klucz regularnie, można to zrobić przy użyciu zresetować klucza na stronie Moje konto.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Wymagane metadane dla elementów opublikowany w galerii programu PowerShell

Galerii programu PowerShell zawiera informacje użytkownikom galerii z pola metadanych, które znajdują się w manifeście skryptu lub module.
Tworzenie lub modyfikowanie elementów dla publikacji w galerii programu PowerShell ma niewielki zestaw wymagań, informacji dostarczonych w manifeście elementu. Zdecydowanie zaleca zapoznanie się sekcji metadanych elementu [wskazówki dotyczące publikowania](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) informacje na temat zawierają najważniejsze informacje dla użytkowników z elementami. 

[ModuleManifest nowy](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) i [ScriptFileInfo nowy](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) poleceń cmdlet utworzy manifestu szablonu, z symbole zastępcze dla manifest elementów. 

Zarówno manifestów ma dwie sekcje, które są ważne w przypadku publikowania, obszar danych klucza podstawowego i PSData PrivateData danymi klucza podstawowego w manifeście modułu programu PowerShell to wszystko poza sekcji PrivateData. Zestawie kluczy podstawowych jest związana z wersji programu PowerShell w użyciu i niezdefiniowana nie są obsługiwane. PrivateData obsługuje dodawanie nowych kluczy, więc PSData elementy specyficzne dla galerii programu PowerShell.


Elementy manifestu najważniejsza, aby wypełnić dla elementu, który można opublikować w galerii programu PowerShell są:  

* Skrypt lub nazwy modułu - te są pobierane z nazwy. PS1 skryptu, lub. PSD1 dla modułu.
* Wersja — jest wymagany klucz podstawowy, format powinien zgodna z wytycznymi programu SemVer (szczegóły najlepsze rozwiązania w zakresie)
* Autor — jest wymagany klucz podstawowy która zawiera nazwę, która ma zostać skojarzony z elementem (zobacz autorzy i właścicieli, poniżej)
* Opis — jest wymagany klucz podstawowy używany do krótko opisano działania tego elementu i wszystkich wymagań dotyczących korzystania z niego
* ProjectURI — jest to zdecydowanie zalecane pole identyfikatora URI w PSData, który zawiera również link do repozytorium Github lub podobne lokalizacji, gdzie czy Programowanie w elemencie.

Autorzy i właścicieli galerii programu PowerShell elementy są powiązane pojęcia, ale nie zawsze odpowiadają.  
Właściciele elementów są użytkownicy z kontami galerii programu PowerShell, które ma uprawnienia do zachowania elementu. Może istnieć wiele właścicieli, kto może zaktualizować dowolny element. Właściciel są dostępne tylko z galerii programu PowerShell i zostaną utracone, jeśli element zostanie skopiowany z jednego systemu do innego. Autor jest ciągiem, który jest wbudowana w manifestu danych, dzięki czemu zawsze jest częścią elementu. Zalecenia dotyczące elementów produktów firmy Microsoft są:

* Ma wiele właścicieli, z co najmniej jednym nazwy zespołu, który spowoduje utworzenie elementu; 
* Mieć autora nazwa dobrze znanego team (na przykład zespołu zestawu SDK platformy Azure) lub Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Wstępne sprawdzanie poprawności tego elementu

Istnieje kilka narzędzi, potrzebnych do uruchomienia kodu przed opublikowaniem tego elementu w galerii programu PowerShell:

* [Analizator skrypt programu PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), która znajduje się w galerii programu PowerShell
* Dla modułów, ModuleManifest testu, który jest częścią środowiska PowerShell
* W przypadku skryptów ScriptFileInfo testu, który jest dostarczany z programu PowerShell Get

[Analizator skrypt programu PowerShell](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) jest narzędzie do analizy kodu statycznych, które skanuje swój kod, aby upewnić się, że spełnia podstawowego środowiska PowerShell wytyczne dotyczące kodowania. To narzędzie określi i najpoważniejszych problemów w kodzie i powinna być uruchamiana regularnie podczas tworzenia pomoże Ci tego elementu jest gotowa do opublikowania. Analizator skrypt programu PowerShell zostanie zawierają listę problemy zidentyfikowane jako błędy, ostrzeżenia i informacje. Wszystkie błędy muszą być kierowane przed opublikowaniem w galerii programu PowerShell. Ostrzeżenia muszą zostać sprawdzone, a większość powinny być kierowane.
Analizator skrypt programu PowerShell jest uruchamiany za każdym razem, gdy element jest opublikowana lub zaktualizowane w galerii programu PowerShell. Zespół operacyjny galerii skontaktuje się z elementu właścicieli, aby usunąć błędy, które zostały znalezione. 

Nie można odczytać manifestu informacji w przedmiot przez infrastrukturę galerii programu PowerShell, nie będzie można opublikować. 
[Test ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) będzie przechwytywać typowe problemy, które mogłoby spowodować module nie można używać podczas instalacji. Musi być uruchamiane dla każdego modułu przed jej opublikowaniem w galerii programu PowerShell. 

Podobnie [ScriptFileInfo testu](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) weryfikuje metadanych za pomocą skryptów i muszą zostać uruchomione na każdy skrypt (opublikowanych oddzielne z modułu) przed jej opublikowaniem w galerii programu Powershell. 


## <a name="publishing-items"></a>Publikowanie elementów

Należy użyć [publikowania skryptu](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) lub [modułu publikowania](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) do publikowania elementów galerii programu PowerShell.
Te polecenia oba wymagają 

* Ścieżka do elementu, który będzie publikować. Dla modułu użyj folder o nazwie modułu. Określ folder, który zawiera wiele wersji tego samego modułu, należy określić RequiredVersion.
* Klucz interfejsu API Nuget. Jest to klucz interfejsu API w stronie Moje konto w galerii programu PowerShell.

Większość pozostałych opcji wiersza polecenia należy w manifestu danych dla elementu, który jest publikowany, więc należy nie należy je określić w poleceniu. 

Aby uniknąć błędów, zdecydowanie zaleca się wypróbować polecenia przy użyciu - Whatif-Verbose, przed opublikowaniem. Spowoduje to zapisanie wiele czasu, ponieważ, za każdym razem, gdy publikowania w galerii programu PowerShell, należy zaktualizować numer wersji w sekcji manifestu elementu. 

Przykładami mogą być: "publikowania modułu — ścieżki". \MyModule "- RequiredVersion"0.0.1"- NugetAPIKey"GUID"- Whatif-Verbose" "publikowania skryptu — ścieżki".\MyScriptFile.PS1"- NugetAPIKey"GUID"- Whatif — pełne"

Należy dokładnie przejrzeć dane wyjściowe, a Jeśli widzisz błędów ani ostrzeżeń, powtórz polecenie bez - Whatif.

Wszystkie elementy, które są publikowane w galerii programu PowerShell ma zostać przeprowadzone skanowanie w poszukiwaniu wirusów i będzie analizować za pomocą analizatora skrypt programu PowerShell. Wszelkie problemy, które pojawiły się w tym czasie będzie wysyłane do wydawcy do rozpoznania.  

Po opublikowaniu elementu w galerii programu PowerShell należy obserwować opinii na temat tego elementu.

* Upewnij się, monitorowanie adresu e-mail skojarzonego z kontem, używany do publikowania.
Użytkownicy, a zespół operacyjny galerii programu PowerShell zostanie wyrazić swoją opinię przy użyciu tego konta, w tym problemów z PSSA lub skanowania antywirusowego.
Jeśli konto e-mail jest nieprawidłowy lub jeśli poważnych problemów są zgłaszane w konta i w lewo nierozpoznane przez długi czas, elementy mogą zostać uwzględnione porzucony i zostanie usunięte z galerii programu PowerShell, zgodnie z opisem w naszym [warunki użytkowania](https://www.powershellgallery.com/policies/Terms).  
* Firma Microsoft zaleca się, że dla każdego elementu w galerii programu PowerShell, który można opublikować subskrybować komentarze. Dzięki temu otrzymasz powiadomienie, jeśli każdy komentarzy w elementów w galerii programu PowerShell. Jest to opcjonalne, ponieważ wymaga utworzenia konta z LiveFyre.     

